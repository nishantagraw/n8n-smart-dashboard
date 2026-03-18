# 🤖 N8N Smart Data Router — WhatsApp AI Agent

> Automatically route WhatsApp messages to Google Calendar, Sheets, Gmail, Drive, Notion, Trello, or Slack using AI.

## 📁 Project Files

| File | Description |
|------|-------------|
| `workflow.json` | **Import this into n8n** — Complete workflow with all 7 destinations |
| `README.md` | This file — Quick start guide |

## 🚀 Quick Start

### 1. Install n8n
```bash
# Option A: Docker (Recommended)
docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n

# Option B: npm
npm install n8n -g && n8n start
```

### 2. Import Workflow
1. Open n8n at `http://localhost:5678`
2. Click **"..."** menu → **"Import from File"**
3. Select `workflow.json`
4. The entire workflow will be imported! 🎉

### 3. Set Up Credentials
Replace these placeholders in the workflow:

| Placeholder | Where to Get |
|------------|-------------|
| `REPLACE_WITH_YOUR_OPENAI_CREDENTIAL_ID` | n8n → Settings → Credentials → OpenAI |
| `REPLACE_WITH_GOOGLE_CALENDAR_CREDENTIAL_ID` | n8n → Settings → Credentials → Google Calendar OAuth2 |
| `REPLACE_WITH_GOOGLE_SHEETS_CREDENTIAL_ID` | n8n → Settings → Credentials → Google Sheets OAuth2 |
| `REPLACE_WITH_YOUR_GOOGLE_SHEET_ID` | From your Google Sheet URL |
| `REPLACE_WITH_GMAIL_CREDENTIAL_ID` | n8n → Settings → Credentials → Gmail OAuth2 |
| `REPLACE_WITH_GOOGLE_DRIVE_CREDENTIAL_ID` | n8n → Settings → Credentials → Google Drive OAuth2 |
| `REPLACE_WITH_GOOGLE_DRIVE_FOLDER_ID` | From your Google Drive folder URL |
| `REPLACE_WITH_WHATSAPP_AUTH_CREDENTIAL_ID` | n8n → Settings → Credentials → Header Auth |
| `REPLACE_WITH_NOTION_CREDENTIAL_ID` | n8n → Settings → Credentials → Notion API |
| `REPLACE_WITH_NOTION_PARENT_PAGE_ID` | From your Notion page URL |
| `REPLACE_WITH_TRELLO_CREDENTIAL_ID` | n8n → Settings → Credentials → Trello API |
| `REPLACE_WITH_TRELLO_LIST_ID` | Trello API (see guide) |
| `REPLACE_WITH_SLACK_CREDENTIAL_ID` | n8n → Settings → Credentials → Slack API |

### 4. Configure WhatsApp Webhook
1. Start ngrok: `ngrok http 5678`
2. Set webhook URL in Meta Developer Dashboard
3. Activate the workflow

## 🧪 Test Without WhatsApp

```bash
curl -X POST http://localhost:5678/webhook-test/whatsapp ^
  -H "Content-Type: application/json" ^
  -d "{\"test_message\": \"Schedule meeting tomorrow at 3pm\", \"from\": \"919999999999\", \"contact_name\": \"Test\"}"
```

## 📊 Supported Categories

| Message Type | Destination | Example |
|-------------|-------------|---------|
| 📅 Dates/Events | Google Calendar | "Meeting with Rahul tomorrow 3pm" |
| 📊 Data/Records | Google Sheets | "Expense: Coffee ₹200" |
| ✉️ Emails | Gmail | "Email john@gmail.com about meeting" |
| 📁 Files/Media | Google Drive | Send any file/image/video |
| 📝 Notes/Ideas | Notion | "Note: We decided to increase budget" |
| 📋 Tasks | Trello | "Task: Review designs by Friday" |
| 💬 Team Updates | Slack | "Notify team: Deploy tonight 10pm" |

## 💰 Cost

| Service | Free Tier |
|---------|-----------|
| n8n (self-hosted) | ✅ Unlimited |
| WhatsApp API | 1,000 conversations/mo |
| OpenAI GPT-4o-mini | ~₹0.15/message |
| Google APIs | ✅ Free |
| Notion/Trello/Slack | ✅ Free tier |

---
Built with ❤️ by Infinite Club
