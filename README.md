# AHMD People — End-to-End AI HR Automation System

AHMD People is a live, production-ready HR automation suite built with **n8n**, **Google Workspace**, and **LLMs (Gemini & Groq)**. It automates candidate intake, AI resume screening, career coaching, and employee policy Q&A through a live web interface.

## Live Project Website
- **Live Demo:** - **Live Demo:** https://Ahmedgamal474.github.io/N8nProtfolio/

## Workflows Overview

| Workflow | Trigger | Description |
| :--- | :--- | :--- |
| **01 - Recruitment Intake** | Form Trigger | Validates PDF CVs, prevents duplicate applications, stores CVs in Google Drive, and logs records in Google Sheets. |
| **02 - AI Screening** | Schedule (Hourly) | Evaluates new applicants against role requirements using AI, updates scores in Sheets, and emails interview invites or declines. |
| **03 - Error Handler** | Error Trigger | Captures execution failures across workflows, logs error details to Google Sheets, and sends email alerts. |
| **04 - Policy Loader** | Startup / Daily / Manual | Syncs HR policy documents from Google Drive into the in-memory vector store for up-to-date RAG retrieval. |
| **05 - RAG HR Assistant** | Chat Trigger | Answers employee policy questions strictly grounded in the uploaded HR documents. |
| **06 - Job Application Coach** | Form Trigger | Analyzes a candidate's CV against a target job description and emails a personalized coaching report. |

## Required Services & Credentials
- **n8n** (Self-hosted via Docker or Cloud)
- **Google Cloud OAuth2** (Google Sheets, Google Drive, Gmail)
- **Google Gemini API** (Embeddings & LLM reasoning)
- **Groq API** (Fast LLM inference for screening and agents)

## How to Import & Run
1. Download the sanitized JSON files from this repository.
2. In your n8n instance, create a project folder and import each `.json` file via **Import from File**.
3. Configure your own **Google OAuth2**, **Gemini**, and **Groq** credentials in n8n.
4. Replace the placeholder IDs (`YOUR_ID`) in Google Sheets and Google Drive nodes with your own Sheet and Folder IDs.
5. Link **03 - Error Handler** in the workflow settings of the other workflows.
6. Activate (Publish) all workflows and run **04 - Policy Loader** once to populate the vector store.