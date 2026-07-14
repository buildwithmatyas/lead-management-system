# AI Lead Management System

> **Portfolio Project**
>
> Demonstrates an AI-powered lead management workflow built with n8n for small business automation.

| Category | Details |
|----------|---------|
| Status | ✅ Complete |
| Platform | n8n |
| AI Model | GPT-4o-mini |
| CRM | Google Sheets |
| Channels | Website Contact Form, Telegram |
| Outputs | Gmail, Telegram |
| Scheduling | Calendly |

---

## Overview

A **production-style** lead management workflow built with **n8n** that captures leads from multiple channels, automatically removes duplicates, qualifies lead urgency using AI, and sends personalized responses based on both the communication channel and lead priority.

**The result:** businesses can reduce lead response time from hours to seconds while maintaining a clean CRM and automatically prioritizing high-intent prospects.

---

## Business Problem

Many small businesses lose potential customers because:

- Leads arrive from multiple sources.
- Duplicate inquiries create messy CRM data.
- Every lead receives the same level of attention.
- Manual lead qualification slows down response times.
- Hot prospects often lose interest before someone follows up.

This workflow automates the complete lead handling process from first contact to customer response.

---

## Solution

Every incoming lead is automatically:

1. Captured from a Website Contact Form or Telegram.
2. Normalized into one shared data structure.
3. Stored in Google Sheets using ContactID deduplication.
4. Classified by OpenAI as **Hot**, **Warm**, or **Cold**.
5. Updated inside the CRM.
6. Routed to the correct communication channel.
7. Sent an appropriate response.
8. If classified as **Hot**, immediately receives a Calendly booking link.

---

## Key Features

- Multi-channel lead capture
- Shared normalized data schema
- Google Sheets CRM integration
- Automatic lead deduplication
- AI-powered lead qualification
- Channel-aware response routing
- Automatic Calendly booking invitation
- Reusable workflow architecture

---

## Workflow Architecture

![Workflow Architecture](screenshots/architecture.png)

---

## Technology Stack

- n8n
- OpenAI GPT-4o-mini
- Google Sheets
- Gmail API
- Telegram Bot API
- Calendly
- Webhooks

---

## Design Decisions

### Why Google Sheets?

Google Sheets provides a lightweight CRM that is easy to deploy for small businesses without requiring additional infrastructure.

### Why ContactID?

ContactID is used as the unique identifier to prevent duplicate records while allowing existing leads to be updated automatically.

### Why AI Qualification?

Rather than treating every inquiry equally, AI prioritizes high-intent prospects so businesses can respond faster where it matters most.

---

## Tested Scenarios

The workflow was tested end-to-end using multiple real-world scenarios.

- ✅ New Website Lead
- ✅ New Telegram Lead
- ✅ Existing Lead (Deduplication)
- ✅ Hot Lead Classification
- ✅ Warm Lead Classification
- ✅ Cold Lead Classification
- ✅ Google Sheets Update
- ✅ Gmail Response
- ✅ Telegram Response
- ✅ Calendly Invitation for Hot Leads

---

## Screenshots

### Google Sheets CRM

![Google Sheets](screenshots/google-sheet.png)

### Gmail Response

![Gmail Response](screenshots/gmail-hot-lead.png)

### Telegram Response

![Telegram Response](screenshots/telegram-response.png)

---

## Project Structure

```text
lead-management-system/
├── workflow/
│   └── lead-management-system.json
├── screenshots/
│   ├── architecture.png
│   ├── google-sheet.png
│   ├── gmail-hot-lead.png
│   └── telegram-response.png
├── docs/
│   └── schema.md
└── README.md
```

---

## Setup

1. Import the workflow into n8n.
2. Connect your own credentials:
   - OpenAI
   - Google Sheets
   - Gmail
   - Telegram Bot
3. Replace the demo Google Sheet with your own.
4. Update the Calendly URL.
5. Activate the workflow.

---

## Future Improvements

- AI-generated personalized responses
- CRM integrations (HubSpot, Airtable)
- Automated follow-up reminders

---

## Contact

If you'd like to discuss this project or connect, feel free to reach out through my GitHub profile or LinkedIn.

---

## Author

Built by **BuildWithMatyas** as part of an AI Automation portfolio focused on practical business workflows using modern AI tools.

This project demonstrates how AI can automate lead qualification, improve response times, and create reusable automation systems for small businesses.
