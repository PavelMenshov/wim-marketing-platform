# WIM Marketing Platform

Overview of the WIM Marketing Agency website and staff dashboard.

The application source is private. This repo explains what the two surfaces do and how they fit together.

## Links

| Surface | URL | For |
|---------|-----|-----|
| Website | [wim-marketing-agency.com](https://www.wim-marketing-agency.com) | Clients and prospects |
| Dashboard | [app.wim-marketing-agency.com](https://app.wim-marketing-agency.com) | Agency staff |

## Docs in this repo

| Doc | Contents |
|-----|----------|
| [docs/website.md](docs/website.md) | Public marketing site |
| [docs/dashboard.md](docs/dashboard.md) | Staff app pages and daily flow |
| [docs/architecture.md](docs/architecture.md) | Hosts, stack, jobs, integrations |

## What WIM built

WIM Marketing Agency runs paid media, analytics, email, and client reporting. The platform has two parts:

1. A **website** for brand, services, and contact.
2. A **dashboard** for drafts, inbox, ads metrics, document search, scheduled jobs, and Telegram alerts.

The system prepares drafts and reports. Staff approve before email or posts go out.

## How the pieces connect

```text
Prospects / clients              Agency staff
        |                              |
        v                              v
   Marketing website              Staff dashboard
   (public pages)                 (login required)
                                         |
                          +--------------+--------------+
                          |              |              |
                       Google         Meta / Ads     Email + bot
                       Gmail Drive    GA4            Mailchimp
                       Calendar                      Telegram
```

## Dashboard features

| Area | What staff get |
|------|----------------|
| Workspaces | One space per client, with modules and account IDs |
| Drafts | Review and approve emails or posts before send |
| Inbox | Recent Gmail threads labeled by priority and tone |
| Knowledge Base | Search client Drive files and help guides (EN / RU) |
| Jobs | Morning briefings, health checks, token refresh, alerts |
| Telegram | Same actions as web chat, plus alerts and reminders |
| Connections | Google and Meta OAuth, credentials stored encrypted |

The in-app Help page is English and Russian. The rest of the UI is English.

## Website features

| Area | What visitors get |
|------|-------------------|
| Brand | Agency identity and services |
| Contact | Path to inquire or start a project |
| Hosting | Own hostname, separate from the staff app |

## Stack

| Layer | Tools |
|-------|-------|
| API and jobs | Python, FastAPI, APScheduler |
| Data | PostgreSQL with pgvector, Redis |
| UI | Server-rendered pages with Tailwind |
| Writing and chat | Claude |
| Document search | Voyage embeddings |
| Deploy | Docker Compose on a VPS with HTTPS |

## Safety rules

| Rule | Detail |
|------|--------|
| Access | Dashboard is staff login only |
| Secrets | OAuth tokens and API keys are encrypted at rest |
| Sending | No auto-send of client email or ads without confirm |
| Mailchimp | Live send needs admin role and a typed confirm phrase |
| Public site | Does not expose operator tools |

## License

These docs are for portfolio and client communication. Product rights stay with WIM Marketing Agency.
