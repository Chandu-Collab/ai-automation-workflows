# 🚀 AI Instagram DM → Lead Capture System (n8n)

Automate your Instagram lead generation using AI.

This workflow captures Instagram DMs, analyzes user intent using AI, and automatically classifies leads into **hot, warm, or cold** — storing them in a CRM and sending instant alerts for high-value leads.

---

## ✨ Features

* 🤖 AI-powered intent detection
* 🔥 Lead classification (Hot / Warm / Cold)
* 📊 Google Sheets CRM integration
* 📩 Instant Gmail alerts for hot leads
* ⚡ Fully automated workflow using n8n

---

## 🧠 How It Works

1. **Instagram DM received**
2. Data sent to n8n via webhook
3. AI agent analyzes message:

   * Detects intent
   * Assigns lead score
4. Leads are routed:

   * 🔥 **Hot leads** → Stored + Email alert
   * 🌤️ **Warm/Cold leads** → Stored in CRM
5. Data stored in Google Sheets

---

## 🛠️ Tech Stack

* n8n (workflow automation)
* OpenAI (AI classification)
* Google Sheets (CRM)
* Gmail (alerts)
* Webhooks (data ingestion)

---

## ⚙️ Setup Guide

### 1. Clone / Import Workflow

* Import the provided n8n JSON file into your n8n instance
* Open workflow in editor

---

### 2. Configure Webhook

* Copy webhook URL from n8n
* Connect it to your Instagram DM source (via ManyChat / API / manual testing)

---

### 3. Set Up OpenAI

* Add your OpenAI API key in n8n credentials
* Ensure AI Agent node is configured properly

---

### 4. Configure Google Sheets

* Create a sheet with columns:

```
Username | Message | Intent | Lead Score | Summary | Status | Created At
```

* Connect Google Sheets node with your account
* Map fields correctly

---

### 5. Configure Gmail Alerts

* Connect Gmail account in n8n
* Set recipient email
* Customize alert message

---

### 6. Test Workflow

Send test payload:

```json
{
  "username": "john_doe",
  "message": "I want pricing",
  "timestamp": "2026-06-19T10:30:00Z"
}
```

Expected:

* Lead classified as **HOT**
* Stored in Google Sheets
* Email alert triggered

---

## 🔀 Workflow Logic

```
Webhook → Normalize Data → AI Agent → Merge → Parse → IF

IF (Hot Lead)
   → Google Sheets
   → Gmail Alert

ELSE
   → Google Sheets
```

---

## 📈 Use Cases

* Instagram lead generation automation
* Agency client handling
* Freelancers managing inquiries
* SaaS onboarding automation

---

## 🚀 Future Improvements

* Auto-reply to Instagram DMs
* Multi-language support
* Lead scoring optimization
* Dashboard for analytics
* CRM integrations (HubSpot, Airtable)

---

## 💬 Want This Workflow?

Comment **"AI"** on my content or reach out to get the full setup.

---

## 📄 License

Free to use and modify for personal and commercial projects.

---

## ⭐ Support

If you found this useful, consider starring ⭐ the repo and sharing it!
