# Pinky Guest List – Collector + Email Notifier

A lightweight guestlist form hosted on GitHub Pages that posts to a Google Apps Script
web app. Submissions are saved to a Google Sheet and a branded email summary (Plum & Gold)
is sent with a CSV attachment.

## How it works
- **Frontend:** `index.html` (static, GitHub Pages)
- **Backend:** Google Apps Script Web App (`doPost`, `doGet`, `doOptions`)
- **Storage:** Google Sheet (tabs: `Submissions`, `Guests`)
- **Email:** `MailApp.sendEmail` sends HTML + plain text + optional CSV

## One-time setup
1. Make a copy of the Google Sheet in your **Gmail** Drive.
2. In Apps Script (Extensions → Apps Script), paste `code.gs`.
3. In `CONFIG`, set:
   - `SHEET_ID` → your Sheet ID (between `/d/` and `/edit` in the Sheet URL)
   - `NOTIFY_EMAILS` → your recipient list
4. Deploy: **Deploy → New deployment → Web app**
   - Execute as: **Me (your Gmail)**
   - Who has access: **Anyone**
   - Copy the `/exec` URL.
5. In the website code, set:
   ```js
   const ENDPOINT = "https://script.google.com/macros/s/XXXXXXXX/exec";
