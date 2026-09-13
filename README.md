# 🧾 AI Invoice Processing Automation

An n8n workflow that watches a Google Drive folder for new invoice PDFs, extracts structured data using AI, logs it to a Google Sheet, and automatically emails a professional billing summary to the finance team.

## 🎯 Problem It Solves
Manually opening invoices, typing details into a spreadsheet, and drafting billing emails is slow and error-prone. This workflow automates the entire pipeline from PDF upload to a ready-to-send billing email.

## ⚙️ Tech Stack
- **n8n** (workflow orchestration)
- **Google Drive Trigger & node** (file watching + download)
- **Extract From File** (PDF text extraction)
- **LangChain Information Extractor** (structured data extraction via Gemini)
- **Google Sheets** (invoice database)
- **LangChain AI Agent** (billing email generation)
- **Gmail** (automated email sending)

## 🔄 How It Works
1. **Trigger** — A Google Drive Trigger watches a specific folder for newly created files.
2. **Download & Extract** — The new PDF is downloaded and its text content is extracted.
3. **Structured Extraction** — An Information Extractor node (powered by Gemini) pulls out invoice number, client name, email, address, phone, total amount, invoice date, and due date.
4. **Logging** — The extracted fields are appended as a new row in a Google Sheet acting as the invoice database.
5. **Email Drafting** — An AI Agent turns the structured invoice data into a formal billing email (with a strict system prompt covering tone, format, and no-hallucination rules).
6. **Sending** — The generated email is sent automatically to the billing/finance address via Gmail.

## 📦 Setup
1. Import `invoice_management.json` into your n8n instance.
2. Connect credentials for:
   - Google Drive OAuth2
   - Google Gemini (PaLM) API
   - Google Sheets OAuth2
   - Gmail OAuth2
3. Point the Google Drive Trigger at your own invoice-upload folder (`YOUR_GOOGLE_DRIVE_FOLDER_ID`).
4. Point the Google Sheets node at your own invoice tracking sheet (`YOUR_GOOGLE_SHEET_ID`) with matching column headers.
5. Update the billing recipient email in the "Send Email" node.
6. Activate the workflow.

> Replace all placeholder values (folder ID, sheet ID, billing email) with your own before running.

## 📈 Impact
Eliminates manual invoice data entry and billing-email drafting, turning a multi-step finance task into a fully automated pipeline triggered by a simple file upload.

## 📄 License
MIT — see [LICENSE](./LICENSE)
