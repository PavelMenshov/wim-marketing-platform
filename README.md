# WIM Marketing Platform

Case study and product overview for **WIM Marketing Agency**.

This repository describes the public website and the internal staff dashboard. Application source stays private.

| Surface | URL | Audience |
|---------|-----|----------|
| Marketing site | [wim-marketing-agency.com](https://www.wim-marketing-agency.com) | Clients and prospects |
| Staff dashboard | [app.wim-marketing-agency.com](https://app.wim-marketing-agency.com) | Agency operators |

---

## What the agency runs

WIM Marketing Agency manages paid media, analytics, email, and client reporting. The platform has two layers:

1. **Website** — brand presence, services, and contact.
2. **Dashboard** — day-to-day operations for account managers: drafts, inbox, ads metrics, knowledge search, scheduled jobs, and Telegram notifications.

Staff approve outbound content before anything reaches a client. The system prepares drafts and reports. People stay in control of send and publish actions.

---

## Product map

```
Clients / prospects          Agency staff
        |                          |
        v                          v
  Marketing website          Staff dashboard
  (public pages)             (login required)
                                   |
                    +--------------+--------------+
                    |              |              |
                 Google        Meta / Ads      Email CRM
                 Workspace     Analytics       (Mailchimp)
                 Gmail Drive   GA4             Telegram bot
                 Calendar
```

More detail: [docs/architecture.md](docs/architecture.md), [docs/website.md](docs/website.md), [docs/dashboard.md](docs/dashboard.md).

---

## Dashboard highlights

- **Workspaces** per client with module toggles (ads, analytics, email, Drive).
- **Draft review** for Gmail, social, and email campaigns. Approve or reject before anything goes out.
- **Inbox helpers** that label recent Gmail threads by priority and tone.
- **Knowledge Base** search over client Drive docs and built-in help guides (English and Russian).
- **Scheduled jobs** for morning briefings, health checks, token refresh, alerts, and weekly digests.
- **Telegram bot** with the same operator actions as the web chat.
- **OAuth connections** for Google and Meta, with encrypted credential storage.

Help Centre inside the app is bilingual (EN / RU). The rest of the product UI is English.

---

## Website highlights

- Agency brand and service positioning
- Contact and inquiry path for new clients
- Separate hostname from the private app (marketing vs operations)

---

## Stack (high level)

| Layer | Choice |
|-------|--------|
| API and jobs | Python, FastAPI, APScheduler |
| Data | PostgreSQL (pgvector for search), Redis |
| UI | Server-rendered dashboard with Tailwind |
| AI | Claude for drafts, briefings, and chat |
| Embeddings | Voyage for document search |
| Hosting | Docker Compose on a VPS behind HTTPS |

---

## Security posture

- Dashboard login for staff only
- Secrets and OAuth tokens encrypted at rest
- No auto-send of client email or ads without an explicit confirm step
- Mailchimp send and schedule require an admin role plus a typed guard phrase
- Public marketing site does not expose operator tools

---

## Related private work

The production automation codebase is private. This repo is the shareable description of what the website and dashboard do, without deployment secrets or internal credentials.

---

## License

Documentation in this repository is provided for portfolio and client communication. All product rights remain with WIM Marketing Agency.
