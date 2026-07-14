# Google Sheets Schema

This workflow uses **Google Sheets** as a lightweight CRM to store and manage incoming leads.

Each row represents a single lead. Existing contacts are automatically updated using **ContactID**, preventing duplicate records while keeping the latest lead information.

---

## Setup Requirements

Before importing the workflow:

- Create a Google Sheet with the column headers listed below.
- **Column names must match exactly.**
- The workflow maps data by column headers, so the column names must match exactly.
- `Replied` and `ReminderSent` are reserved for future workflow extensions and should remain in the sheet.

---

## Schema

| Column          | Type     | Description                                                                                    |
| --------------- | -------- | ---------------------------------------------------------------------------------------------- |
| LeadID          | Number   | Unique identifier for each lead.                                                               |
| Name            | Text     | Lead's full name.                                                                              |
| Email           | Text     | Lead's email address (may be empty for Telegram leads).                                        |
| Message         | Text     | Original inquiry submitted by the lead.                                                        |
| Date            | DateTime | Timestamp when the lead was received.                                                          |
| Replied         | Boolean  | Indicates whether the lead has been replied to. Reserved for future workflow extensions.       |
| ReminderSent    | Boolean  | Indicates whether a follow-up reminder has been sent. Reserved for future workflow extensions. |
| LeadScore       | Text     | AI-generated lead classification: **Hot**, **Warm**, or **Cold**.                              |
| ContactID       | Text     | Unique identifier used for deduplication.                                                      |
| DeliveryChannel | Text     | Source channel (`email` or `telegram`).                                                        |
| Contact         | Text     | Contact value used when sending responses (email address or Telegram identifier).              |

---

## ContactID Format

The workflow generates `ContactID` based on the source channel.

| Channel  | Example                  |
| -------- | ------------------------ |
| Website  | `john.smith@example.com` |
| Telegram | `telegram_demo_user`     |

This value is used by the CRM node to detect existing contacts and update them instead of creating duplicate rows.

---

## Example Record

| LeadID        | Name       | Email                  | Message | Date                 | LeadScore | ContactID              | DeliveryChannel |
| ------------- | ---------- | ---------------------- | ------- | -------------------- | --------- | ---------------------- | --------------- |
| 1784023389227 | John Smith | john.smith@example.com | Hello   | 2026-07-14T12:03:09Z | Cold      | john.smith@example.com | email           |

---

## AI Classification

Each lead is automatically classified by OpenAI into one of three priority levels:

| LeadScore | Description                                                              |
| --------- | ------------------------------------------------------------------------ |
| 🔴 Hot    | High purchase intent. Receives an immediate Calendly booking invitation. |
| 🟡 Warm   | Interested lead requiring standard follow-up.                            |
| 🔵 Cold   | Low-priority inquiry or general question.                                |

---

## Notes

This schema was intentionally designed to be lightweight and easy to adapt.

Although this project uses Google Sheets as a lightweight CRM, the workflow can easily be adapted to platforms such as **Airtable**, **HubSpot**, **Notion**, or other CRM systems.
