import requests
import pandas as pd
from datetime import datetime, timedelta
import os
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
from email.mime.base import MIMEBase
from email import encoders

# ===============================
# CONFIGURAÇÕES
# ===============================

SEARCH_TERM = "Penaeus vannamei"
CSV_PATH = "dados/artigos.csv"

EMAIL_REMETENTE = "SEU_EMAIL"
EMAIL_SENHA = "SUA_SENHA"
EMAIL_DESTINO = "EMAIL_DESTINO"

# ===============================
# BUSCAR ARTIGOS (1 dias)
# ===============================

def buscar_artigos():

    if os.path.exists(CSV_PATH):
        df_existente = pd.read_csv(CSV_PATH)
        if not df_existente.empty:
            ultima_data = df_existente["data"].max()
        else:
            ultima_data = (datetime.today() - timedelta(days=1)).strftime("%Y-%m-%d")
    else:
        ultima_data = (datetime.today() - timedelta(days=1)).strftime("%Y-%m-%d")

    url = "https://api.openalex.org/works"

    params = {
        "search": SEARCH_TERM,
        "filter": f"from_publication_date:{ultima_data}",
        "per_page": 50
    }

    response = requests.get(url, params=params)
    data = response.json()

    artigos = []

    for work in data.get("results", []):
        artigos.append({
            "data": work.get("publication_date"),
            "titulo": work.get("title"),
            "doi": work.get("doi")
        })

    return pd.DataFrame(artigos)

# ===============================
# SALVAR SEM DUPLICAR
# ===============================

def salvar_novos(df_novos):

    if not os.path.exists("dados"):
        os.makedirs("dados")

    if os.path.exists(CSV_PATH):
        df_existente = pd.read_csv(CSV_PATH)
    else:
        df_existente = pd.DataFrame(columns=["data", "titulo", "doi"])

    # Remover artigos sem DOI
    df_novos = df_novos.dropna(subset=["doi"])

    # Identificar apenas DOIs novos
    novos_reais = df_novos[~df_novos["doi"].isin(df_existente["doi"])]

    # Atualizar base completa
    df_final = pd.concat([df_existente, novos_reais])
    df_final.to_csv(CSV_PATH, index=False)

    return novos_reais

# ===============================
# ENVIAR EMAIL COM ANEXO
# ===============================

def enviar_email(df_novos):

    msg = MIMEMultipart()
    msg["From"] = EMAIL_REMETENTE
    msg["To"] = EMAIL_DESTINO
    msg["Subject"] = f"Atualização sobre {SEARCH_TERM}"

    if df_novos.empty:
        corpo = "Nenhum artigo novo encontrado nos últimos 30 dias."
    else:
        corpo = "Novos artigos encontrados:\n\n"
        for _, row in df_novos.iterrows():
            corpo += f"{row['data']} - {row['titulo']}\n"
            corpo += f"{row['doi']}\n\n"

    msg.attach(MIMEText(corpo, "plain"))

     # anexar CSV
    with open(CSV_PATH, "rb") as attachment:
        part = MIMEBase("application", "octet-stream")
        part.set_payload(attachment.read())

    encoders.encode_base64(part)
    part.add_header(
        "Content-Disposition",
        "attachment; filename=artigos_atualizados.csv",
    )

    msg.attach(part)

    with smtplib.SMTP_SSL("smtp.gmail.com", 465) as server:
        server.login(EMAIL_REMETENTE, EMAIL_SENHA)
        server.send_message(msg)

    print("Email enviado com sucesso.")

# ===============================
# EXECUÇÃO
# ===============================

if __name__ == "__main__":
    df_busca = buscar_artigos()
    df_novos = salvar_novos(df_busca)
    enviar_email(df_novos)

    print(f"{len(df_novos)} novos artigos adicionados.")
