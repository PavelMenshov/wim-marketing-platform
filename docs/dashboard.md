# Staff dashboard

Private application for WIM account managers and admins.

**URL:** https://app.wim-marketing-agency.com

## Who uses it

| Role | Typical work |
|------|----------------|
| Account manager | Review drafts, check inbox, ask the bot for reports |
| Admin | Connect OAuth, manage workspaces, run Mailchimp send with confirmation |

UI language is English. Help Centre content is available in English and Russian.

## Main areas

| Page | Purpose |
|------|---------|
| Dashboard | Today’s pending drafts, alerts, inbox, spend snapshot |
| Workspaces | Client list, modules, connection status, IDs |
| AI Chat | Same capabilities as the Telegram bot, in the browser |
| Drafts | Approve or reject prepared emails and posts |
| Content | Social / content variants awaiting review |
| Inbox | Classified Gmail threads by client |
| Meetings | Calendar context and pre-meeting notes |
| Reminders | Operator reminders delivered in Telegram |
| Jobs | Status of scheduled automations |
| Alerts | Ads anomalies |
| Activities | Event feed (drafts, job outcomes, approvals) |
| Knowledge Base | Search client documents and help guides |
| Help | Bilingual operator guide |

## Connected services (by client)

Not every client uses every channel. Examples of how modules map:

| Service | Typical use |
|---------|-------------|
| Google (Gmail, Drive, Calendar, GA4) | Inbox, files, meetings, traffic |
| Meta Ads | Paid social performance for selected clients |
| Google Ads | Search performance for selected clients |
| Mailchimp | Email performance reports and guarded campaign actions |
| Telegram | Health pings, alerts, chat commands for staff |

## Operator flow

1. Morning health ping arrives in Telegram.
2. Open **Drafts** and read each item fully.
3. Approve only when the text and attachments are correct.
4. Use **Inbox** or chat if a client thread needs attention.
5. Ask chat or Telegram for ads / GA4 / Mailchimp summaries when preparing updates.

Nothing client-facing leaves the system without an explicit approve (or an admin-confirmed Mailchimp action).

## Telegram

Staff can use natural language or short commands, for example:

- show pending drafts
- Mailchimp monthly report for a named client
- Google Ads summary for the last 7 days
- search Drive or Knowledge Base
- set a reminder

The bot mirrors the web chat tools. Final publish and send still respect the same approval rules.
