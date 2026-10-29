# Kesiena Micah Irikefe

**Full-stack developer and application security engineer. I build Next.js/TypeScript systems with enforced authorization boundaries, then break them the way an attacker would.**

<p align="left">
  <a href="https://micahkesiena.vercel.app"><b>Portfolio</b></a> •
  <a href="https://micahkesiena.vercel.app/#contact"><b>Contact</b></a> •
  <a href="https://x.com/DevTech_Coder23"><b>X</b></a> •
  <a href="https://github.com/DevTechMike-Coder?tab=repositories"><b>All repositories</b></a>
</p>

> **Availability:** <!-- TODO: pick one and delete the rest -->
> Open to freelance full-stack builds, security-focused code reviews, and scoped web/API penetration tests (written authorization required).
> Also considering full-time roles in AppSec / full-stack. Reach me through the [contact form](https://micahkesiena.vercel.app/#contact).

---

## Focus

- **Authorization correctness:** object-level access control (IDOR/BOLA), RBAC, server-side enforcement on every mutation.
- **Session and auth security:** OAuth 2.0 + PKCE, signed session cookies, rotation, expiry, revocation.
- **Hardened upload and input pipelines:** magic-byte validation, size/type allowlists, rate limiting, strict CSP.
- **Vulnerability analysis:** logic-flaw review, CVSS scoring, triage workflows.

---

## Featured Projects

### [Vertex Canvas](https://github.com/DevTechMike-Coder/KanbanTool)
Real-time kanban workspace with notifications, team management, and file storage.

<!-- TODO: add screenshot/GIF + live demo link -->
<!-- ![Vertex Canvas](./docs/vertex-demo.gif) -->
[Live demo](https://vertexcanvas.vercel.app/) · [Threat model](https://github.com/DevTechMike-Coder/KanbanTool/blob/main/docs/threat-model.md) · [SECURITY.md](https://github.com/DevTechMike-Coder/KanbanTool/blob/main/SECURITY.md)

[![CodeQL](https://github.com/DevTechMike-Coder/KanbanTool/actions/workflows/codeql.yml/badge.svg)](https://github.com/DevTechMike-Coder/KanbanTool/actions/workflows/codeql.yml)
[![CI](https://github.com/DevTechMike-Coder/KanbanTool/actions/workflows/ci.yml/badge.svg)](https://github.com/DevTechMike-Coder/KanbanTool/actions/workflows/ci.yml)

**Security controls (each links to the implementation):**

| Control | Implementation | Evidence |
|---|---|---|
| Authentication | Supabase Auth; Google/GitHub via OAuth 2.0 + PKCE (S256) | [`lib/auth/oauth.ts`](https://github.com/DevTechMike-Coder/KanbanTool/blob/main/lib/auth/oauth.ts) |
| Sessions | HMAC-SHA256 signed cookies, Edge-verifiable. Expiry/revocation limits documented in the threat model | [`lib/auth/session.ts`](https://github.com/DevTechMike-Coder/KanbanTool/blob/main/lib/auth/session.ts) |
| Authorization (IDOR/BOLA) | Resource → project → team membership check on every task/project server action | [`app/actions/tasks.ts`](https://github.com/DevTechMike-Coder/KanbanTool/blob/main/app/actions/tasks.ts) · authz regression tests <!-- TODO link --> |
| File uploads | Extension allowlist, magic-byte validation, 20 MB cap, per-user object path | [`app/api/upload/route.ts`](https://github.com/DevTechMike-Coder/KanbanTool/blob/main/app/api/upload/route.ts) |
| Rate limiting | Redis (`ioredis`) → PostgreSQL atomic upsert → in-memory fallback, per-IP on auth actions | [`lib/auth/rate-limit.ts`](https://github.com/DevTechMike-Coder/KanbanTool/blob/main/lib/auth/rate-limit.ts) |
| Security headers | HSTS, `X-Frame-Options: DENY`, `nosniff`, Referrer-Policy, CSP (nonce-based CSP on the roadmap) | [`next.config.ts`](https://github.com/DevTechMike-Coder/KanbanTool/blob/main/next.config.ts) |

`nextjs` `typescript` `prisma` `postgresql` `supabase` `tailwindcss` `oauth-pkce` `idor-protection`

---

### [VulnTrack Lite](https://github.com/DevTechMike-Coder/VulnTrack-Lite)
Vulnerability management and analysis engine: track, filter, and score findings across software ecosystems.

<!-- TODO: add screenshot + live demo link -->
[Live demo](#) · [SECURITY.md](https://github.com/DevTechMike-Coder/VulnTrack-Lite/blob/main/SECURITY.md)

[![CodeQL](https://github.com/DevTechMike-Coder/VulnTrack-Lite/actions/workflows/codeql.yml/badge.svg)](https://github.com/DevTechMike-Coder/VulnTrack-Lite/actions/workflows/codeql.yml)

- CVSS score (0.0–10.0) and severity stored per CVE; severity is currently entered, not derived from the score
- Pydantic-validated API, parameterized SQLite queries, HTML-escaped rendering. Local single-user tool: see the threat model before exposing it
- Modular SQLite layer
- **Roadmap:** NVD ingestion, CISA KEV flagging, EPSS-based prioritization <!-- move to "Shipped" as implemented -->

`python` `fastapi` `sqlite` `cvss` `vulnerability-management`

---

## Security Work

<!-- TODO: replace with real, sanitized entries. Remove any row you can't back up. -->

| Type | Item | Link |
|---|---|---|
| Writeup | <!-- sanitized pentest / code-review / lab writeup --> | [link](#) |
| Platform | <!-- HTB / TryHackMe / PortSwigger Academy profile + progress --> | [link](#) |
| Recognition | <!-- CVE / bounty / hall-of-fame, if any --> | [link](#) |
| Certifications | <!-- list or "in progress: X" --> | |

**Tooling:** <!-- keep only what you actually use --> Burp Suite · OWASP ZAP · nmap · ffuf · sqlmap · Wireshark · Bash · Python

**Ethics:** testing is limited to systems I own, lab environments, and targets under written authorization.

---

## Client Work

### [E&A Atelier](https://eaatelier.vercel.app/): luxury artisanal e-commerce storefront
Dynamic catalog, responsive cart, editorial layout.

- **Outcomes:** Lighthouse <!-- TODO: Perf/A11y/SEO/BP scores --> · <!-- TODO: load-time or feature results -->
- **Testimonial:** <!-- TODO: quote + attribution, or remove -->
- [Live site](https://eaatelier.vercel.app/) · [Repository](https://github.com/DevTechMike-Coder/E-A_Atelier)
- `nextjs` `react` `typescript` `tailwindcss`

<!-- TODO: add a second project, or keep heading as "Selected Client Work" -->

---

## Stack

| Area | Tools |
|---|---|
| Frontend | Next.js (App Router), React, TypeScript, Tailwind CSS, Framer Motion, GSAP, dnd-kit |
| Mobile | React Native, Expo |
| Backend | Next.js server actions/route handlers, Hono, FastAPI, BullMQ |
| Data | PostgreSQL, Prisma, Drizzle ORM, Supabase, SQLite |
| Auth & Security | OAuth 2.0/PKCE, session hardening, RBAC, CSP, rate limiting |

---

## Currently

<!-- TODO: update monthly -->
- **Building: Clone[ An Instagram/Twitter Style Clone]** 
- **Researching: COMPTIA A** 
- **Learning: Docker Desktop** 

---

## How I Use AI

AI tools accelerate prototyping and debugging. All generated code is reviewed by hand, checked against OWASP ASVS, and covered by tests before it ships.

---

## Collaboration

Interested in: full-stack apps with complex authorization or real-time needs; API security research and vulnerability tooling; security reviews of open-source React/Next.js and Python projects. Use the [contact form](https://micahkesiena.vercel.app/#contact).

<p align="center">
  <i>© 2026 Kesiena Micah Irikefe</i>
</p>
