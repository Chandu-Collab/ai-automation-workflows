# AI Cold Email Personalization Engine

## Overview

The **AI Cold Email Personalization Engine** is an end-to-end n8n workflow that automates personalized B2B outreach.

Instead of sending generic cold emails, this workflow researches a company's website, analyzes its business using AI, generates a tailored outreach email, sends it through Gmail, and records the execution in Google Sheets.

If a company website is unavailable, the workflow automatically falls back to a professional generic outreach email.

---

# Workflow Goals

* Automate cold email outreach
* Personalize every email using AI
* Reduce manual research time
* Maintain outreach logs
* Support businesses with or without websites

---

# Key Features

* Webhook-based lead intake
* Company website scraping
* AI-powered business analysis
* Personalized subject generation
* Personalized email generation
* Gmail integration
* Google Sheets logging
* Automatic fallback for missing websites
* Production-ready workflow structure

---

# Technology Stack

| Component        | Technology    |
| ---------------- | ------------- |
| Workflow Engine  | n8n           |
| AI Model         | OpenAI        |
| Website Scraping | Apify         |
| Email Service    | Gmail         |
| Data Storage     | Google Sheets |
| Trigger          | Webhook       |

---

# Workflow Architecture

```
Webhook
    │
    ▼
Normalize Lead Data
    │
    ▼
Website Available?
    │
 ┌──┴─────────────┐
 │                │
Yes              No
 │                │
 ▼                ▼
Website       Generic Email
Scraping          Flow
 │
 ▼
Aggregate Website Content
 │
 ▼
AI Business Research
 │
 ▼
Store Business Insights
 │
 ▼
AI Email Generator
 │
 ▼
Merge Lead + Email Data
 │
 ▼
Gmail
 │
 ▼
Webhook Response
```

---

# Input Format

The workflow accepts a POST request through a Webhook.

Example:

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "company": "Example Technologies",
  "website": "https://example.com"
}
```

---

# Workflow Stages

## 1. Receive Lead Data

The workflow starts when a webhook receives lead information.

Fields:

* Name
* Email
* Company
* Website

---

## 2. Normalize Lead Data

Standardizes incoming fields for use throughout the workflow.

---

## 3. Website Validation

Checks whether a website URL exists.

### If Available

Continue with AI research.

### If Missing

Skip research and generate a professional fallback email.

---

## 4. Company Website Scraping

Uses Apify to extract website content.

Collected information includes:

* Homepage
* Services
* About
* Business overview
* Brand messaging

---

## 5. Aggregate Website Content

Combines scraped pages into a single document to improve AI analysis.

---

## 6. AI Business Research

Analyzes the website and extracts:

* Company Name
* Business Summary
* Industry
* Services
* Target Audience
* Unique Selling Points
* Possible Business Challenges
* Brand Tone
* Compliment
* Personalization Hook

Example Output:

```json
{
  "company_name": "",
  "business_summary": "",
  "industry": "",
  "services": [],
  "target_audience": "",
  "unique_selling_points": [],
  "pain_points": [],
  "brand_tone": "",
  "compliment": "",
  "personalization_hook": ""
}
```

---

## 7. Store Business Insights

Business insights are logged in Google Sheets for auditing and reuse.

Suggested columns:

* Timestamp
* Lead Name
* Email
* Company
* Website
* Industry
* Business Summary
* Services
* Target Audience
* Pain Points
* Unique Selling Points
* Brand Tone
* Compliment
* Personalization Hook

---

## 8. AI Cold Email Generator

Generates:

* Personalized Subject
* Personalized Email

The AI uses:

* Lead Name
* Company
* Business Research
* Pain Points
* Personalization Hook
* Compliment

Example Output:

```json
{
  "subject": "",
  "email": ""
}
```

---

## 9. Gmail Integration

Automatically sends the generated email.

Includes:

* Recipient
* Subject
* Email Body

---

## 10. Fallback Flow

If no website is provided:

* Skip website scraping
* Skip business research
* Generate a professional cold email using only the lead name and company
* Send through Gmail

This ensures every lead receives an email.

---

# Required Credentials

## OpenAI

Used for:

* Business Analysis
* Email Generation

---

## Apify

Used for:

* Website scraping

---

## Gmail

Used for:

* Sending personalized emails

---

## Google Sheets

Used for:

* Logging business insights

---

# Expected Results

For each lead the workflow:

1. Receives lead information
2. Researches the business (if website exists)
3. Generates AI insights
4. Creates a personalized subject
5. Creates a personalized cold email
6. Sends the email
7. Stores business insights
8. Returns a successful webhook response

---

# Business Benefits

* Eliminates manual company research
* Improves cold email personalization
* Saves outreach time
* Increases scalability
* Maintains a searchable record of AI-generated insights

---

# Future Enhancements

* CRM Integration (HubSpot, Salesforce, Zoho)
* LinkedIn profile enrichment
* Company news analysis
* AI lead scoring
* Multi-language email generation
* Human approval before sending
* Email open and reply tracking
* Automated follow-up sequences
* Analytics dashboard
* A/B testing for subject lines

---

# Best Practices

* Validate webhook input before processing.
* Use AI only with verified website content.
* Do not infer facts that cannot be supported.
* Keep prompts consistent for reliable structured output.
* Log all executions for troubleshooting and reporting.
* Secure API keys using n8n credentials.

---

# Workflow Summary

The AI Cold Email Personalization Engine enables businesses to automate personalized outreach at scale by combining website intelligence, AI-driven analysis, email generation, Gmail automation, and structured logging into a single production-ready workflow.
