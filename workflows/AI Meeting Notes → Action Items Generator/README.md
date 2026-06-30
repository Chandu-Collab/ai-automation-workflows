# AI Meeting Notes & Action Items Generator

## Version

**Version:** 1.0 (Phase-1)

---

# Overview

The **AI Meeting Notes & Action Items Generator** is an n8n workflow that automatically converts meeting transcripts into structured meeting summaries, extracts key decisions and action items, stores the results in Google Sheets, and sends a professional meeting summary via email.

This workflow eliminates the need for manual meeting documentation while ensuring every action item is captured and shared.

---

# Problem Statement

After every meeting, teams typically spend valuable time:

* Reading lengthy meeting transcripts
* Writing summaries
* Identifying action items
* Assigning owners
* Recording deadlines
* Sending follow-up emails

This repetitive process is time-consuming and often leads to missed tasks.

---

# Solution

This workflow automates the complete post-meeting documentation process using AI.

The workflow:

* Receives a meeting transcript
* Uses AI to understand the discussion
* Generates a meeting summary
* Extracts key decisions
* Identifies action items
* Assigns owners
* Detects deadlines
* Stores every task in Google Sheets
* Sends a formatted meeting summary email

---

# Workflow Architecture

```
Webhook
    │
    ▼
Prepare Meeting Data
    │
    ▼
AI Meeting Analysis
    │
    ▼
Validate Structured Output
    │
    ▼
Split Action Items
    │
    ▼
Format Task Records
    │
    ▼
Google Sheets
    │
    ▼
Aggregate Results
    │
    ▼
Generate Email Summary
    │
    ▼
Merge Request + AI Output
    │
    ▼
Send Email
```

---

# Features

* AI Meeting Summary
* Key Decision Extraction
* Action Item Detection
* Owner Identification
* Deadline Detection
* Priority Assignment
* Google Sheets Integration
* Automated Email Summary
* Webhook API Support
* Reusable Workflow

---

# Required Credentials

## OpenAI

Used for meeting analysis.

Required:

* API Key

---

## Google Sheets

Stores extracted tasks.

Required:

* Google OAuth Credential

---

## Gmail

Sends the meeting summary.

Required:

* Gmail OAuth Credential

---

# Workflow Nodes

## 1. Receive Meeting Request

Receives incoming meeting data using a webhook.

Method:

POST

Expected payload:

```json
{
  "meetingTitle": "Sprint Planning",
  "meetingDate": "2026-06-25",
  "participants": [
    "John",
    "Alice",
    "Bob"
  ],
  "email": "manager@example.com",
  "transcript": "Meeting transcript..."
}
```

---

## 2. Prepare Meeting Data

Keeps only the required fields before sending data to the AI.

Fields:

* meetingTitle
* meetingDate
* participants
* email
* transcript

---

## 3. AI Meeting Analysis

The AI analyzes the transcript and extracts:

* Meeting Summary
* Key Decisions
* Action Items
* Owners
* Deadlines
* Priority

The AI returns structured JSON.

Example:

```json
{
  "summary": "...",
  "decisions": [],
  "tasks": [
    {
      "task": "",
      "owner": "",
      "deadline": "",
      "priority": ""
    }
  ]
}
```

---

## 4. Validate Structured Output

Ensures the AI response matches the expected schema before continuing.

---

## 5. Split Action Items

Splits every extracted task into an individual item.

Example:

Task 1

Task 2

Task 3

---

## 6. Format Task Records

Maps task fields into a clean structure suitable for database storage.

Output:

* Summary
* Decision
* Task
* Owner
* Deadline
* Priority

---

## 7. Save Tasks to Google Sheets

Each action item is stored as an individual row.

Example:

| Summary | Decision | Task | Owner | Deadline | Priority |
| ------- | -------- | ---- | ----- | -------- | -------- |

---

## 8. Combine Meeting Results

Rebuilds all tasks into a single object for email generation.

---

## 9. Generate Email Summary

Creates a professional meeting report.

Example:

Meeting Summary

Key Decisions

Action Items

Owner

Deadline

Priority

---

## 10. Merge Email Payload

Combines:

* Original webhook request
* Generated email content

This allows the email recipient to come directly from the webhook request instead of being hardcoded.

---

## 11. Send Meeting Summary

Sends the generated meeting report to the provided email address.

---

# Google Sheets Structure

Recommended columns:

| Meeting Summary | Decision | Task | Owner | Deadline | Priority |

---

# Sample Input

```json
{
  "meetingTitle": "Sprint Planning",
  "meetingDate": "2026-06-25",
  "participants": [
    "John",
    "Alice",
    "Bob"
  ],
  "email": "manager@example.com",
  "transcript": "John will complete the login API by Friday. Alice will design the dashboard by Monday. Bob will test the deployment before release. We decided to use PostgreSQL instead of MySQL."
}
```

---

# Sample AI Output

```json
{
  "summary": "Sprint Planning meeting covered upcoming work items.",
  "decisions": [
    "Use PostgreSQL instead of MySQL"
  ],
  "tasks": [
    {
      "task": "Complete the login API",
      "owner": "John",
      "deadline": "Friday",
      "priority": "Medium"
    },
    {
      "task": "Design the dashboard",
      "owner": "Alice",
      "deadline": "Monday",
      "priority": "Medium"
    },
    {
      "task": "Test the deployment before release",
      "owner": "Bob",
      "deadline": "Before Release",
      "priority": "Medium"
    }
  ]
}
```

---

# Email Output

Subject

```
Meeting Summary & Action Items
```

Body

```
Meeting Summary

Sprint Planning meeting covered upcoming work items.

-------------------------------------

Key Decision

• Use PostgreSQL instead of MySQL

-------------------------------------

Action Items

1. John

Task:
Complete the login API

Deadline:
Friday

Priority:
Medium

2. Alice

Task:
Design the dashboard

Deadline:
Monday

Priority:
Medium

3. Bob

Task:
Test the deployment before release

Deadline:
Before Release

Priority:
Medium
```

---

# API Response

Example success response:

```json
{
  "status": "success",
  "message": "Meeting processed successfully.",
  "tasksCreated": 3,
  "emailSent": true
}
```

---

# Workflow Benefits

* Eliminates manual meeting documentation
* Reduces administrative work
* Improves task tracking
* Provides consistent meeting summaries
* Creates structured records
* Easy integration with existing systems
* Reusable via Webhook API

---

# Use Cases

* Sprint Planning
* Daily Standups
* Client Meetings
* Sales Calls
* HR Interviews
* Team Meetings
* Project Kickoffs
* Internal Discussions

---

# Future Enhancements (Phase-2)

Potential improvements include:

* Automatic meeting transcription
* Calendar integration
* Slack notifications
* Microsoft Teams integration
* Jira task creation
* ClickUp integration
* Notion integration
* AI confidence scoring
* Follow-up reminders
* Multi-language support
* Meeting sentiment analysis
* Duplicate task detection

---

# Technology Stack

* n8n
* OpenAI
* Google Sheets
* Gmail
* Webhooks
* JSON API

---

# Conclusion

The AI Meeting Notes & Action Items Generator is a practical business automation workflow that transforms meeting transcripts into actionable outputs with minimal manual effort.

It demonstrates AI-powered information extraction, workflow orchestration, structured data processing, cloud integrations, and automated communication, making it suitable for teams, agencies, startups, and enterprises looking to streamline post-meeting workflows.
