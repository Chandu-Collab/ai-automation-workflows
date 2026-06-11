# 🚀 AI YouTube Content Repurposer

Convert any YouTube video into multi-platform content using AI.

This n8n workflow takes a YouTube link and automatically generates:

* ✍️ LinkedIn Post
* 📸 Instagram Caption + Reel Script
* 🐦 Twitter Thread
* 📝 Blog Article
* 📧 Sends everything directly to your email

---

## 🎥 Demo

> Paste a YouTube link → Get content for 4 platforms instantly 🤯

([https://youtu.be/DDjlBYK-9Yk?si=0RAYXI8DJSkF9bUs])

---

## ⚙️ Tech Stack

* **n8n** – Workflow automation
* **Apify** – YouTube transcript extraction
* **NVIDIA API** – LLM (`meta/llama-3.1-70b-instruct`)
* **SMTP** – Email delivery

---

## 📁 Project Structure

```
workflow/
  └── youtube-content-repurposer.json

assets/
  ├── workflow-screenshot.png
  ├── output-email.png
  └── thumbnail.png

docs/
  └── setup.md
```

---

## ⚙️ Setup Instructions

### 🔑 1. Apify API (Transcript)

Actor used:

```
starvibe~youtube-video-transcript
```

* Create account → https://apify.com/
* Copy API token
* Add in transcript node

---

### 🤖 2. NVIDIA API (LLM)

Model used:

```
meta/llama-3.1-70b-instruct
```

* Get API key → https://build.nvidia.com/
* Add in all AI HTTP nodes

---

### 📧 3. Email Setup

Use SMTP (Gmail recommended):

* Host: `smtp.gmail.com`
* Port: `465`
* Secure: `true`

Use **App Password** (not your Gmail password)

---

## 📥 Input Format

Send a POST request:

```json
{
  "youtube_url": "https://www.youtube.com/watch?v=VIDEO_ID",
  "email": "your@email.com"
}
```

---

## 🚀 How It Works

1. Extracts video transcript using Apify
2. Cleans and processes transcript
3. Generates structured insights using AI
4. Creates platform-specific content
5. Merges all outputs
6. Sends results via email

---

## 🎯 Use Cases

* Content creators
* Social media managers
* Developers exploring AI automation
* Marketing workflows

---

## 💡 Future Improvements

* Frontend UI
* Auto-post to social platforms
* Multi-language support
* Database integration

---

## 🤝 Support

If you want this workflow or need help setting it up:

👉 Reach out or open an issue

---

## ⭐ If you found this useful

Give it a star ⭐ and share it with others!
