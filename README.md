# ResumeParsingAIAgent
# 🧠 ResumeParsingAIAgent – Smart Resume Screening with n8n & GPT-4

This repository contains an end-to-end AI-driven resume screening system built with **n8n**. It automates candidate evaluation by scoring resumes against job descriptions using **OpenAI GPT**, logging results to **Google Sheets**, and emailing qualified candidates.

## 📂 Project Structure

This repo includes three n8n workflows:

| File Name                               | Description |
|----------------------------------------|-------------|
| `JD Intake.json`                       | Captures job description input and stores it for scoring. |
| `Resume Intake & Parsing Agent.json`   | Handles resume upload and parsing. |
| `Score Resume Against JD.json`         | Scores resume against the stored job description using GPT, returns score + reason and and logging to Google Sheets.|

---

## 🔁 How It Works

1. 📝 A **recruiter** submits a Job Description via the JD Intake workflow.
2. 📎 A **candidate** uploads their resume and selects a role via the frontend.
3. 📄 The resume is parsed and sent to **GPT-4**, along with the job description.
4. 🔢 GPT returns a **score (0–10)** and **reasoning**.
5. 📊 Results are **logged in Google Sheets**.
6. ✅ If the score is **greater than 6**, the candidate is emailed a **Calendly interview link**.

---

## 🧠 GPT Prompting Logic

- Resumes are compared with the submitted JD.
- GPT evaluates based on skill match, experience, and language.
- The final score and explanation are returned in structured JSON.

---

## 🛠 Requirements

- n8n (self-hosted or cloud)
- OpenAI API Key
- Google Sheets API credentials
- Gmail SMTP credentials
- A Calendly link (for interview scheduling)

---

## ⚙️ Setup Instructions

1. **Clone this repo** or download the JSON workflows.
2. **Import all `.json` files** into your n8n instance.
3. Set up these credentials in n8n:
   - `openai` – GPT API key
   - `googleSheets` – Access to your evaluation spreadsheet
   - `smtp` – Gmail (or other) email service for interview invites
4. Update:
   - Google Sheet ID and tab name
   - Job role options and Calendly link
5. Deploy the form frontend (Softr, HTML, etc.) to allow resume uploads and role selection.

---

## 📊 Sample Google Sheet Output

| Candidate Name | Role | Score | Reason | Resume Link | Status |
|----------------|------|-------|--------|-------------|--------|
| Jane Doe       | Data Analyst | 7.5 | Good match on SQL, Tableau, and statistics | [View](#) | Interview Sent |
| John Smith     | Backend Dev  | 4.0 | Missing backend stack knowledge | [View](#) | Logged |

---

## 📬 Email Example

```text
Subject: You're Invited to Interview!

Hi [Candidate Name],

Thanks for applying to [Startup Name]! Based on your resume, we'd love to move forward.

Please schedule your interview here: [Calendly Link]

Looking forward to speaking with you.

– [Startup Name] Team
