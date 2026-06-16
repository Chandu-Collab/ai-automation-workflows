# 🤖 Multilingual AI Customer Support Automation (n8n)

Automate your customer support using AI agents with multilingual capabilities.

This workflow detects the language of incoming emails, understands user intent, and either replies automatically or escalates the issue — all without manual intervention.

---

## 🚀 Features

* 🌐 Multilingual support (Hindi, Telugu, English, and more)
* 🤖 AI-powered intent classification (Refund, Technical Issue, Complaint, etc.)
* 💬 Automatic response generation
* 🚨 Smart escalation for high-priority queries
* 🔁 Replies in the user’s original language
* 📩 Gmail integration for end-to-end automation

---

## 🧠 Workflow Overview

```text
Gmail → Language Detection → Translation → Classification → Decision
        → Auto Reply (User)
        → Escalation (Admin)
```

---

## ⚙️ Tech Stack

* **n8n** – Workflow automation
* **OpenAI / LLM** – AI Agents
* **Gmail API** – Email integration

---

## 📦 Setup Instructions

### 1. Import Workflow

* Open n8n
* Import the provided workflow JSON

---

### 2. Configure Gmail

* Connect your Gmail account
* Enable:

  * Read Emails (Trigger)
  * Send Emails (Reply/Escalation)

---

### 3. Configure AI Agents

* Add your OpenAI (or compatible LLM) API key
* Attach credentials to all AI Agent nodes

---

### 4. Verify Agents

| Agent              | Purpose                              |
| ------------------ | ------------------------------------ |
| Language Detection | Detects language + confidence        |
| Translation        | Converts input to English            |
| Classification     | Identifies category + urgency        |
| Reply Agent        | Generates response                   |
| Final Translation  | Converts reply back to user language |

---

### 5. Test the Workflow

Send emails like:

* **English:** I want a refund
* **Hindi:** मुझे मेरा पैसा वापस चाहिए
* **Telugu:** నాకు నా డబ్బు తిరిగి కావాలి

---

## 🚦 Decision Logic

* High urgency OR low confidence → 🚨 Escalation
* Otherwise → 🤖 Auto Reply

---

## 📧 Output Behavior

### Auto Reply

* Sent to user
* In original language

### Escalation

* Sent to admin
* Includes full context

---

## 🧪 Example Flow

```text
User (Hindi) → AI detects language → translates → classifies → generates reply → translates back → sends email
```

---

## ⚠️ Notes

* Use one query per email for best results
* Avoid mixed-language inputs
* Ensure all fields (message, email, subject, language) are passed correctly

---

## 🔮 Future Improvements

* 📊 Logging (Google Sheets / DB)
* ⏱️ Response time tracking
* 📈 Analytics dashboard
* 🔔 Slack/Discord alerts
* 📱 WhatsApp integration

---

## 🎬 Demo

Check out the demo videos on Instagram / YouTube Shorts.

---

## 🏁 Conclusion

This project demonstrates how AI + automation can:

* Reduce manual support effort
* Improve response time
* Enable global (multilingual) customer support

---

## 💡 Author

Built with ❤️ using n8n and AI Agents.

---

## ⭐ If you like this project

Give it a star ⭐ and share your feedback!
