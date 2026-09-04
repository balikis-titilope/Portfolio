# Project Overview

## What this is

A single-page portfolio site for a **Full-Stack Developer Building
AI-Powered Products**. It leads with full-stack breadth — frontend, backend,
APIs, payments, deployment — and uses AI integration as the specialization
that differentiates it from a generic full-stack portfolio.

**File**: `portfolio.html` — a single static HTML file, no build step. Open
it directly in a browser or deploy it as-is to any static host (Vercel,
Netlify, GitHub Pages, S3, etc.).

## Positioning

```
Full-Stack Developer
  → builds SaaS & production web applications
  → strong backend + frontend experience
  → specializes in AI integrations and AI-powered features
  → can also handle APIs, payments, automation, deployment
```

> FULL-STACK DEVELOPER · AI & SAAS
> I build the product, not just one piece of it.
> From frontend and backend architecture to AI integrations, APIs, payments, and deployment — I build complete web products that are ready to ship.

The goal is for a visitor to leave thinking **"this person can build the
whole product, and they know how to integrate AI into it"** — not "this
person makes AI demos." Leading with full-stack widens the pool of clients
this site can win (anyone needing a web app, not only anyone needing AI)
while the three Featured Work projects still make AI the standout skill.

## Structure — 7 sections, in order

1. **Hero** — role label, headline, one-line framing ("full-stack is the
   foundation, AI is the specialization"), six core-area tags, two CTAs, and
   a compact 3-column strip linking to the three AI-flagship projects.
2. **Featured Work** — the three AI-flagship products: **FlowDesk**,
   **LeadScore AI**, **AuraPM**. Each is numbered (01–03), shows a role line,
   a short pitch, tech tags, and a small abstract product mockup. Clicking a
   card opens a modal with the full case study: role → problem → solution →
   highlights → stack.
3. **Real-World Experience** — four production projects at real companies
   (**AffPilot**, **Luggage Forward**, **Test Psycho**, **First Circle**),
   numbered 04–07, shown as simpler rows (title, role, description, tags —
   no mockup, no modal). This is the proof that the work extends beyond
   AI-flagship side projects into shipped, production systems.
4. **Skills & Tools** — four grouped categories instead of one long list:
   AI & Intelligent Systems, Full-Stack Development, Backend & Data,
   Integrations & Infrastructure.
5. **How I Work** — a 4-step process (Understand → Design → Build → Ship).
6. **CTA** — dark closing block: "Have a product you want to build?" with a
   single primary action and an availability line.
7. **Footer** — minimal, name/year + GitHub/LinkedIn/email links.

## The seven projects

### Featured Work (case-study modal, numbered 01–03)

| # | Project | Role | One-line pitch |
|---|---|---|---|
| 01 | **FlowDesk** | Full-Stack Developer · AI Integration | AI customer support agent combining a SaaS interface with RAG and knowledge-base retrieval. |
| 02 | **LeadScore AI** | Full-Stack Developer · AI Integration | AI lead qualification system using structured outputs and backend business rules to surface hot leads. |
| 03 | **AuraPM** | Full-Stack Developer · AI Integration | AI assistant embedded directly in a project-management SaaS, scoped to real project data. |

Full case-study copy (role/problem/solution/highlights/stack) lives in the
`projects` object in `portfolio.html`'s `<script>` — see **AGENTS.md** before
editing it.

### Real-World Experience (simple rows, numbered 04–07)

| # | Project | Role | Demonstrates |
|---|---|---|---|
| 04 | **AffPilot** | Backend Developer | Backend engineering, APIs, SaaS, automation, integrations |
| 05 | **Luggage Forward** | Backend Developer | Backend engineering, APIs, business logic, production systems |
| 06 | **Test Psycho** | Full-Stack Developer | React, frontend + backend development, APIs |
| 07 | **First Circle** | Backend Developer · Stripe Integration · Deployment | Backend engineering, Stripe, payments, deployment, production launch |

This content is inline HTML (no JS object) — edit directly in the
`.exp-item` blocks.

## Skills grouping

Instead of a flat 25-technology list, skills are organized into four cards:

- **AI & Intelligent Systems** — AI Integration, OpenAI API, LLM
  Applications, RAG Systems, AI Assistants, AI Workflows, Structured AI
  Outputs, AI Automation
- **Full-Stack Development** — React, Next.js, TypeScript, Node.js, NestJS,
  Python, FastAPI, REST APIs
- **Backend & Data** — PostgreSQL, MongoDB, MySQL, Redis, API Development,
  Authentication, Business Logic
- **Integrations & Infrastructure** — Stripe, Third-Party APIs, Webhooks,
  Docker, AWS, CI/CD, Deployment, Production Debugging

## Visual direction

Modern AI-SaaS aesthetic — closer to Linear or Vercel than a typical
"passionate developer" portfolio. Specifically:

- Warm off-white background, near-black text, one blue accent used sparingly
- `Space Grotesk` for headings, `IBM Plex Sans` for body, `IBM Plex Mono` for
  labels/tags/role lines
- Hairline borders instead of card shadows; minimal, consistent border-radius
- Left-aligned, asymmetric layout rather than centered hero blocks
- One deliberate animation (the hero's load-in sequence) — everything else
  is a hover/click response, not scroll-triggered decoration

Full design-token reference and the rules for keeping edits on-brand are in
**AGENTS.md**.

## Launch Checklist Status

- [x] Real name, email, domain, GitHub, LinkedIn, and Upwork profile links (`balqees.dev@gmail.com`, `balikis-titilope`, Upwork profile)
- [x] Real screenshots for LeadScore AI and AuraPM in `assets/` (FlowDesk using clean CSS mockup)
- [x] Real-World Experience companies linked to live platforms (AffPilot, Luggage Forward, Test Psycho, First Circle)
- [x] Availability line in CTA section configured

Note: outcome metrics were intentionally removed from the Featured Work
modals — there's no fabricated data anywhere on the site currently. If you
have real numbers for FlowDesk, LeadScore AI, or AuraPM, they can be added
back into the modal as a genuine highlight.

## Related files

- `portfolio.html` — the site itself
- `AGENTS.md` — architecture, design tokens, and rules for any AI agent
  editing this project (read before making changes)
