# Architecture

## Hosts

| Host | Role |
|------|------|
| `www.wim-marketing-agency.com` | Marketing website |
| `app.wim-marketing-agency.com` | Staff dashboard and OAuth callbacks |

Staff use the app host for drafts, ads checks, and inbox. Prospects use the website only.

## App runtime

```text
Browser / Telegram
        |
        v
   FastAPI app
   - web UI
   - REST API
   - scheduled jobs
        |
   +----+----+
   |         |
Postgres   Redis
(search)   (cache, job history)
```

Outbound calls go to Google, Meta, Mailchimp, Voyage, and Claude. Credentials are encrypted per client workspace.

## Workspaces

Each client is a workspace. A workspace holds:

| Item | Examples |
|------|----------|
| Modules | Gmail, Drive, Calendar, GA4, Meta Ads, Google Ads, Mailchimp |
| Account IDs | Ads customer id, GA4 property id |
| Credentials | OAuth tokens or API keys for that client |

Jobs and chat tools load the matching credentials before they call an external API.

## Scheduled jobs (Hong Kong time)

| Job | When | Purpose |
|-----|------|---------|
| Morning briefing | Daily | Client snapshot for staff |
| Health ping | Daily | Status message in Telegram |
| Token refresh | Every 30 min | Keep OAuth sessions valid |
| Knowledge ingest | Nightly | Index Drive docs for search |
| Inbox classifier | On an interval | Label recent Gmail threads |
| Performance alerts | Hourly | Flag unusual ads metrics |
| Weekly / monthly reports | On cron | Performance packages for clients |

Telegram gets health pings, alerts, digests, and draft reminders. The web app is where staff review and approve.

## AI and search

| Tool | Used for |
|------|----------|
| Claude | Drafts, briefings, chat replies, tool calls for metrics and search |
| Voyage | Embeddings for document search |

Drive folders with many images can be skipped during ingest so indexing stays on PDFs and Docs.

## Defaults that protect clients

| Default | Behavior |
|---------|----------|
| Drafts | Start as pending. Approve is required to send or publish. |
| Mailchimp in chat | Read-only reports. Live send sits in an admin screen with confirm. |
| Demo mode | Full UI with sample data when real ad accounts are not connected. |
