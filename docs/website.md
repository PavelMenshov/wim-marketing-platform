# Marketing website

Public brand site for WIM Marketing Agency.

**URL:** https://www.wim-marketing-agency.com

## Role

The website introduces the agency, services, and contact path. It is separate from the staff dashboard so prospects and operators never share the same login surface.

## Relationship to the dashboard

| Concern | Website | Dashboard |
|---------|---------|-----------|
| Audience | Public | Staff |
| Content | Brand, services, contact | Operations tools |
| Auth | None for browsing | Staff login |
| Host | `www` | `app` |

OAuth callbacks and automation APIs point at the `app` host only.

## Design notes

The dashboard visual language follows the agency site (light background, high-contrast type, restrained chrome) so daily tools feel like part of the same brand. Marketing pages stay focused on storytelling and inquiry. The app stays focused on tasks: drafts, inbox, reports, and jobs.
