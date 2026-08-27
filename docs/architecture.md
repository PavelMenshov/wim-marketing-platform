# Architecture overview

## Two public surfaces

WIM keeps brand and operations on different hosts.

| Host | Role |
|------|------|
| `www.wim-marketing-agency.com` | Marketing website |
| `app.wim-marketing-agency.com` | Staff dashboard and OAuth callbacks |

Operators never need the marketing CMS to approve a draft or check ads. Prospects never see the dashboard login.

## Runtime shape

```
Browser / Telegram
        |
        v
   FastAPI app
   - /web UI
   - /api/v1 integrations
   - scheduled jobs
        |
   +----+----+
   |         |
Postgres   Redis
(pgvector) (cache, job history)
```

Integrations talk outbound to Google, Meta, Mailchimp, Voyage, and Claude. Credentials are stored encrypted per workspace.

## Workspace model

Each client is a **workspace** with:

- enabled modules (Gmail, Drive, Calendar, GA4, Meta Ads, Google Ads, Mailchimp, …)
- account IDs where needed (ads customer id, GA4 property id)
- OAuth or API credentials for that client context

Jobs and chat tools resolve the right credentials from the workspace before calling an external API.

## Daily automation

Examples of scheduled work (Hong Kong time):

| Job | Cadence | Purpose |
|-----|---------|---------|
| Morning briefing | Daily | Client snapshot for staff |
| Health ping | Daily | Telegram status for the operator |
| Token refresh | Every 30 min | Keep OAuth sessions alive |
| Knowledge ingest | Nightly | Sync Drive docs into searchable chunks |
| Inbox classifier | Interval | Label recent Gmail threads |
| Performance alerts | Hourly | Flag unusual ads metrics |
| Weekly / monthly reports | Cron | Client-facing performance packages |

Telegram receives health pings, alerts, digests, and draft reminders. The web dashboard is the place for careful review and approval.

## AI usage

Claude prepares drafts, briefings, and chat replies. It can call tools for ads metrics, GA4, Mailchimp reports, Drive search, and knowledge search.

Embeddings (Voyage) power semantic search over documents. Image-heavy Drive folders can be skipped so ingest focuses on PDFs and Docs until vision spend is intentional.

## Safety defaults

- Drafts start as pending. Approve is required to send or publish.
- Chat tools that read Mailchimp are read-only. Live send lives in an admin UI with confirmation.
- Demo mode can run the full UI with fixtures when real ad accounts are not connected.
