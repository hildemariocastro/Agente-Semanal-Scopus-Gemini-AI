🧠 Overview

AI Research Intelligence System is a modular automation framework designed to monitor, process and summarize scientific publications related to Penaeus vannamei / Litopenaeus vannamei.

The system integrates:

Scientific APIs (Scopus & OpenAlex)

Generative AI (Google Gemini)

Automated reporting

Persistent data storage

Email notification pipeline

It transforms raw scientific publications into structured, actionable research intelligence.

🎯 Problem Statement

Scientific production in aquaculture grows continuously.
Manual literature monitoring is:

Time-consuming

Prone to duplication

Difficult to maintain consistently

Hard to scale

This system automates the entire process.

🏗 System Architecture
Module 1 – Scopus + Gemini (Weekly Intelligence Report)

Scopus API
→ Metadata extraction
→ Abstract processing
→ Gemini AI summarization
→ Structured DOCX report
→ Email distribution

Module 2 – OpenAlex (Daily Monitoring Engine)

OpenAlex API
→ Date filtering
→ DOI validation
→ Duplicate detection
→ CSV persistence layer
→ Email alert

⚙ Core Capabilities

Automated scientific search

DOI-based duplicate prevention

AI-driven technical summarization

Persistent research database

Scheduled execution

Modular architecture

Email notification engine

Research-grade analytical summaries

🧪 Technology Stack
Layer	Technology
Language	Python
Scientific API	Scopus (Pybliometrics)
Open API	OpenAlex
AI Engine	Google Gemini (google.genai)
Data Handling	Pandas
Reporting	python-docx
Storage	CSV (Expandable to SQLite)
Notification	SMTP (Gmail App Password)
🔍 AI Integration Strategy

This project was developed using generative AI as an engineering assistant.

The development process included:

Author-defined architecture

Manual prompt engineering

Iterative debugging

Validation of outputs

API error handling adjustments

Performance optimization

Logical flow redesign when needed

Generative AI was used as a productivity tool, not as a replacement for technical reasoning.

All logic validation, testing, debugging and architectural decisions were performed by the author.

📂 Project Structure
ai-research-intelligence/
│
├── scopus_gemini_agent.py
├── openalex_daily_agent.py
├── requirements.txt
├── README.md
│
├── dados/
│   └── artigos.csv
│
├── reports/
│   └── Relatorio_Vannamei_YYYY-MM-DD.docx
│
└── logs/

🚀 Installation
pip install -r requirements.txt

🔐 Environment Configuration

Use environment variables instead of hardcoding secrets:

GEMINI_API_KEY=
EMAIL_USER=
EMAIL_PASSWORD=

▶ Execution
Run Weekly Scopus + Gemini Report
python scopus_gemini_agent.py

Run Daily OpenAlex Monitor
python openalex_daily_agent.py

⏱ Automation

Supports:

Windows Task Scheduler

Cron (Linux/Mac)

Server deployment

Cloud execution (future roadmap)

📄 Output Examples
Weekly Intelligence Report

Structured DOCX

Technical analytical summary

Research-level interpretation

DOI references

Practical aquaculture implications

Daily Alert

New publications only

Duplicate-proof

DOI-based filtering

CSV updated automatically

📊 Engineering Highlights

API rate-limit awareness

Duplicate prevention via DOI hash comparison

Error-handling for SMTP authentication

Modular prompt structure for research-grade summaries

Abstract-length validation before AI processing

Scalable design for multi-keyword expansion

🛡 Security Considerations

No API keys stored in repository

.gitignore configured

App Password required for email

Secrets managed via environment variables

📈 Roadmap

SQLite persistence layer

Multi-keyword monitoring

Research topic classification via AI

Citation trend tracking

Streamlit dashboard

Docker containerization

Cloud deployment

ESG monitoring module

👨‍🔬 Author

Hildemario Castro
Engineer | Aquaculture Research | AI Automation Developer

