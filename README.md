# AI Research Intelligence System

> An automated research intelligence framework for monitoring, processing, summarizing, and reporting scientific publications on *Penaeus vannamei* and *Litopenaeus vannamei*.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Active-success.svg)
![AI](https://img.shields.io/badge/Powered%20by-Google%20Gemini-orange.svg)

---

# Overview

The **AI Research Intelligence System** is a modular automation framework designed to continuously monitor scientific publications related to *Penaeus vannamei* (*Litopenaeus vannamei*), automatically process publication metadata, generate AI-powered technical summaries, maintain a persistent publication database, and distribute research reports via email.

The project integrates modern scientific APIs with Generative AI to transform raw scientific literature into structured, actionable research intelligence.

---

# Motivation

Scientific production in aquaculture has grown exponentially over the last decade. Monitoring newly published articles manually has become increasingly difficult because it is:

- Time-consuming
- Difficult to maintain consistently
- Prone to duplicated records
- Hard to scale over long periods

This project automates the complete literature surveillance workflow.

---

# Key Features

- Automated scientific literature monitoring
- Integration with Scopus API
- Integration with OpenAlex API
- AI-powered technical summaries using Google Gemini
- Duplicate detection using DOI validation
- Persistent publication database
- Automated DOCX report generation
- Email notification system
- Modular architecture
- Ready for scheduled execution
- Easily expandable to additional research topics

---

# System Architecture

```text
                        +----------------------+
                        |   Scientific APIs    |
                        |----------------------|
                        |  Scopus  | OpenAlex |
                        +----------+-----------+
                                   |
                                   |
                          Metadata Collection
                                   |
                                   ▼
                      Duplicate Detection (DOI)
                                   |
                                   ▼
                     Persistent Publication Storage
                                   |
                                   ▼
                     Google Gemini AI Processing
                                   |
                                   ▼
                     Technical Research Summaries
                                   |
                 +-----------------+-----------------+
                 |                                   |
                 ▼                                   ▼
        Weekly DOCX Report                 Daily Email Alert
```

---

# Modules

## Module 1 — Weekly Intelligence Report

Pipeline:

```
Scopus API
      ↓
Metadata Extraction
      ↓
Abstract Processing
      ↓
Google Gemini
      ↓
Technical Summary
      ↓
DOCX Report
      ↓
Email Distribution
```

Produces a research-grade weekly intelligence report containing:

- publication metadata
- AI-generated summaries
- DOI references
- practical implications
- analytical insights

---

## Module 2 — Daily Monitoring Engine

Pipeline:

```
OpenAlex API
       ↓
Today's Publications
       ↓
DOI Validation
       ↓
Duplicate Detection
       ↓
CSV Database Update
       ↓
Email Notification
```

Only newly published articles are reported.

---

# Technology Stack

| Layer | Technology |
|---------|------------|
| Language | Python |
| Scientific Database | Scopus API |
| Open Database | OpenAlex |
| AI Engine | Google Gemini |
| Data Processing | Pandas |
| Report Generation | python-docx |
| Storage | CSV (SQLite-ready) |
| Notifications | SMTP (Gmail App Password) |

---

# Project Structure

```
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
├── logs/
│
└── .gitignore
```

---

# Installation

Clone the repository:

```bash
git clone https://github.com/yourusername/ai-research-intelligence.git
```

Enter the project folder:

```bash
cd ai-research-intelligence
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# Environment Variables

Never hardcode credentials.

Create a `.env` file containing:

```text
GEMINI_API_KEY=your_api_key

EMAIL_USER=your_email@gmail.com

EMAIL_PASSWORD=your_app_password

SCOPUS_API_KEY=your_scopus_api_key
```

---

# Usage

## Weekly Scopus Intelligence Report

```bash
python scopus_gemini_agent.py
```

Generates:

- DOCX report
- AI technical summaries
- Email delivery

---

## Daily OpenAlex Monitoring

```bash
python openalex_daily_agent.py
```

Checks:

- new publications
- duplicate DOIs
- updates CSV database
- sends notification email

---

# Output Examples

## Weekly Intelligence Report

- Microsoft Word (.docx)
- Publication metadata
- AI-generated technical summaries
- DOI references
- Practical implications for aquaculture
- Research interpretation

---

## Daily Alert

Contains only newly identified publications.

Features:

- DOI validation
- Duplicate prevention
- Automatic database update
- Email notification

---

# Engineering Highlights

- Modular architecture
- AI-assisted scientific summarization
- DOI-based duplicate detection
- Robust SMTP authentication handling
- API rate-limit awareness
- Abstract length validation
- Research-oriented prompt engineering
- Easily scalable for multiple research topics

---

# AI Integration

Generative AI was used as an engineering assistant throughout the development process.

Applications included:

- prompt engineering
- code generation
- debugging assistance
- workflow optimization
- API integration support
- documentation drafting

All architectural decisions, validation, testing, debugging, and final implementation were designed and verified by the project author.

Generative AI functioned as a productivity tool rather than a substitute for technical reasoning.

---

# Security

Security best practices implemented:

- API keys are never stored in the repository
- `.gitignore` excludes sensitive files
- Gmail App Password authentication
- Environment variable configuration
- No credentials committed to version control

---

# Roadmap

Future planned features include:

- SQLite persistence layer
- PostgreSQL support
- Multi-keyword monitoring
- AI-based topic classification
- Citation trend analysis
- Interactive Streamlit dashboard
- Docker container
- Cloud deployment
- ESG monitoring module
- Automatic systematic review support
- Semantic similarity search
- Research recommendation engine

---

# Contributing

Contributions are welcome.

If you would like to improve this project:

1. Fork the repository.
2. Create a feature branch.

```bash
git checkout -b feature/new-feature
```

3. Commit your changes.

```bash
git commit -m "Add new feature"
```

4. Push the branch.

```bash
git push origin feature/new-feature
```

5. Open a Pull Request.

---

# Citation

If you use this project in academic research, please cite it appropriately.

Example:

```text
Castro, H.
AI Research Intelligence System.
GitHub Repository.
```

---

# License

This project is licensed under the MIT License.

See the `LICENSE` file for details.

---

# Author

**Hildemario Castro**

Aquaculture Researcher • Data Scientist • AI Automation Developer

Areas of interest:

- Aquaculture
- Fisheries Science
- Histology
- Scientometrics
- Artificial Intelligence
- Machine Learning
- Scientific Automation

---

## Acknowledgements

This project was developed to support reproducible, automated scientific monitoring workflows for aquaculture research and demonstrates the integration of modern scientific databases, artificial intelligence, and research automation into a scalable intelligence framework.
