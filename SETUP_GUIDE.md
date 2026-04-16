# DataReport Setup Guide

## Quick Setup (5 minutes)

### Step 1: Download Files
Files you need:
- `index.html` — The web app
- `n8n_workflow.json` — Automation workflow
- `report_history_template.csv` — Google Sheets template

### Step 2: Setup Google Sheets

1. Go to [sheets.google.com](https://sheets.google.com)
2. Create new spreadsheet, name it "DataReport"
3. Add these column headers in row 1:
   ```
   Timestamp | Username | Email | FileName | RowCount | ColumnNames | AvgValues
   ```
4. Copy the spreadsheet ID from the URL:
   ```
   https://docs.google.com/spreadsheets/d/YOUR_SHEET_ID_HERE/edit
   ```

### Step 3: Setup n8n

1. Open n8n (`n8n` in terminal)
2. Create new workflow
3. Click the three dots menu → **Import from JSON**
4. Paste contents of `n8n_workflow.json`
5. Edit these nodes:
   - **Webhook**: Copy the webhook URL
   - **Google Sheets**: Paste your Sheet ID and connect Google account
   - **Email**: Add your SMTP credentials (Gmail works with App Password)
6. Click **Activate**

### Step 4: Update index.html

1. Open `index.html` in a text editor
2. Find line with `N8N_WEBHOOK_URL` (around line 320)
3. Replace `YOUR_N8N_WEBHOOK_URL` with your n8n webhook URL
4. Find `GOOGLE_SHEET_ID` and paste your Google Sheet ID

### Step 5: Run!

Open `index.html` in browser, or host on GitHub Pages/Netlify.

---

## Features

- **Dark aesthetic UI** with smooth animations
- **Drag & drop** file upload
- **Auto-parses** CSV and Excel files
- **Generates charts** with Chart.js
- **Saves history** to Google Sheets
- **Sends email** reports (via n8n)
- **Multi-user** support

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| "Connection error" | Check n8n is running and webhook URL is correct |
| File not parsing | Make sure file is valid CSV format |
| Email not sending | Verify SMTP credentials in n8n |
| Google Sheets not saving | Reconnect Google account in n8n |
