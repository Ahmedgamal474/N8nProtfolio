# n8n AI Automation Portfolio

A collection of production-ready AI automation workflows built with **n8n**, **Google Workspace**, **WhatsApp Cloud API**, **Telegram**, and **LLMs (Gemini & Groq)**.

## Live Project Website
- **Live Demo:** https://ahmedgamal474.github.io/N8nProtfolio/

---

## Project 1: AHMD People — End-to-End AI HR Automation

| Workflow | Trigger | Description |
| :--- | :--- | :--- |
| **01 - Recruitment Intake** | Form Trigger | Validates PDF CVs, prevents duplicate applications, stores CVs in Google Drive, and logs records in Google Sheets. |
| **02 - AI Screening** | Schedule (Hourly) | Evaluates new applicants against role requirements using AI, updates scores in Sheets, and emails interview invites or declines. |
| **03 - Error Handler** | Error Trigger | Captures execution failures across workflows, logs error details to Google Sheets, and sends email alerts. |
| **04 - Policy Loader** | Startup / Daily / Manual | Syncs HR policy documents from Google Drive into the in-memory vector store for up-to-date RAG retrieval. |
| **05 - RAG HR Assistant** | Chat Trigger | Answers employee policy questions strictly grounded in the uploaded HR documents. |
| **06 - Job Application Coach** | Form Trigger | Analyzes a candidate's CV against a target job description and emails a personalized coaching report. |

---

## Project 2: Dawaa دواء — Smart Pharmacy WhatsApp & Telegram Assistant

| Workflow | Trigger | Description |
| :--- | :--- | :--- |
| **DawaaResv** | WhatsApp & Telegram Triggers | Reads medicine requests or prescription photos via Gemini Vision, fuzzy-matches against the Google Sheets catalog, auto-reserves OTC items for 2 hours, and routes controlled/unclear items to a pharmacist on Telegram with inline Approve/Reject buttons. |
| **Dawaa2Error** | Schedule & Error Triggers | Runs a 15-minute sweep to expire uncollected reservations and restore stock, sends a nightly low-stock reorder list at 22:00, and classifies/logs runtime errors. |

---

## How to Import & Run
1. Download the sanitized JSON files from this repository.
2. In your n8n instance, create a project folder and import each `.json` file via **Import from File**.
3. Configure your own **Google OAuth2**, **Gemini**, **Groq**, **WhatsApp Cloud API**, and **Telegram Bot** credentials in n8n.
4. Replace the placeholder IDs (`YOUR_...`) in Google Sheets, Google Drive, WhatsApp, and Telegram nodes with your own IDs.
5. Link the respective Error Handler workflow in the workflow settings and activate (Publish) all workflows.