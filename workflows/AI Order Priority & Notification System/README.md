# 🚀 AI Order Priority & Notification System (n8n Workflow)

## 📌 Overview

This workflow automates e-commerce order handling using AI.

It captures new orders, analyzes them using an AI agent, classifies priority (High / Medium / Low), sends email notifications, and logs all data into Google Sheets.

---

## ⚡ Features

* ✅ Automatic order capture via webhook
* 🤖 AI-based priority classification
* 📧 Email notifications based on priority
* 📊 Real-time logging in Google Sheets
* ⚙️ Fully automated workflow using n8n

---

## 🧠 Workflow Logic

1. A new order is received via webhook
2. Order data is cleaned and structured
3. AI agent analyzes the order
4. Priority is assigned:

   * 🔴 High → urgent
   * 🟡 Medium → normal
   * 🟢 Low → non-urgent
5. Email notification is sent accordingly
6. Order is stored in Google Sheets

---

## 🧱 Workflow Architecture

```
Webhook Trigger
   ↓
Set (Normalize Data)
   ↓
AI Agent (Priority Classification)
   ↓
Set (Parse AI Output)
   ↓
Switch (Route by Priority)
   ├── High → Email → Google Sheets
   ├── Medium → Email → Google Sheets
   └── Low → Email → Google Sheets
```

---

## 📥 Input Format

```json
{
  "order_id": "ORD123",
  "customer_name": "John",
  "email": "john@example.com",
  "order_value": 12000,
  "delivery_type": "express"
}
```

---

## 🧠 AI Logic

Priority is determined using:

* High:

  * order_value > 10000 OR delivery_type = "express"
* Medium:

  * order_value between 3000 and 10000
* Low:

  * order_value < 3000

---

## 📧 Email Notifications

* 🔴 High Priority
  → Immediate alert email

* 🟡 Medium Priority
  → Standard notification

* 🟢 Low Priority
  → Informational / low urgency

---

## 📊 Google Sheets Logging

Each order is stored with:

* Order ID
* Customer Name
* Email
* Order Value
* Delivery Type
* Priority
* Timestamp

---

## 🛠️ Tech Stack

* n8n (workflow automation)
* OpenAI (AI classification)
* Gmail (email notifications)
* Google Sheets (data logging)

---

## 🚀 Use Cases

* E-commerce stores
* Dropshipping businesses
* Order management systems
* Operations automation

---

## 🔮 Future Enhancements (Phase-2)

* AI reasoning (why priority was assigned)
* Processing time tracking (SLA)
* VIP customer detection
* Confidence scoring
* Analytics dashboard

---

## 💡 How to Use

1. Import workflow into n8n
2. Configure:

   * OpenAI API key
   * Gmail credentials
   * Google Sheets connection
3. Start webhook
4. Send test order
5. Monitor automation

---

## 📣 Call to Action

If you found this useful:

⭐ Star the repo
💬 Comment “AI” to get the workflow
🚀 Follow for more automation ideas

---

## 🧾 License

This project is open for learning and customization.

---

## 🙌 Credits

Built using n8n + AI automation concepts.
