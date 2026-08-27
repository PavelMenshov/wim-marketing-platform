# Staff dashboard

Private app for WIM account managers and admins.

**URL:** https://app.wim-marketing-agency.com

## Users

| Role | Usual work |
|------|------------|
| Account manager | Review drafts, check inbox, ask the bot for reports |
| Admin | Connect OAuth, manage workspaces, confirm Mailchimp send |

UI language is English. Help content is English and Russian.

## Pages

| Page | Purpose |
|------|---------|
| Dashboard | Pending drafts, alerts, inbox, spend summary |
| Workspaces | Clients, modules, connection status, IDs |
| AI Chat | Browser chat with the same tools as Telegram |
| Drafts | Approve or reject prepared emails and posts |
| Content | Social drafts waiting for review |
| Inbox | Gmail threads grouped by client |
| Meetings | Calendar context and notes before calls |
| Reminders | Reminders delivered in Telegram |
| Jobs | Status of scheduled automations |
| Alerts | Unusual ads metrics |
| Activities | Feed of drafts, job results, approvals |
| Knowledge Base | Search client files and help guides |
| Help | Operator guide in EN and RU |

## Services by client

Modules are turned on per workspace. Common mappings:

| Service | Use |
|---------|-----|
| Google (Gmail, Drive, Calendar, GA4) | Inbox, files, meetings, traffic |
| Meta Ads | Paid social metrics for selected clients |
| Google Ads | Search metrics for selected clients |
| Mailchimp | Email reports and confirmed campaign actions |
| Telegram | Health pings, alerts, chat for staff |

## Daily flow

1. Health ping arrives in Telegram in the morning.
2. Open Drafts and read each item in full.
3. Approve only when text and attachments look right.
4. Use Inbox or chat when a client thread needs attention.
5. Ask chat or Telegram for ads, GA4, or Mailchimp summaries when writing updates.

Client-facing send needs an explicit approve, or an admin confirm for Mailchimp.

## Telegram examples

Staff can type short requests such as:

- show pending drafts
- Mailchimp monthly report for a named client
- Google Ads summary for the last 7 days
- search Drive or Knowledge Base
- set a reminder

The bot uses the same tools as web chat. Publish and send still follow the approval rules above.
