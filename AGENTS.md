# AGENTS.md

Instructions for any AI agent (Claude, Cursor, Copilot, etc.) editing this project.
Read this before making changes. When in doubt, match what already exists in
`portfolio.html` rather than introducing something new.

## What this project is

A single-file static portfolio site (`portfolio.html`) for a **Full-Stack
Developer Building AI-Powered Products**. No build step, no package manager,
no framework. Open the file in a browser and it works.

Do not turn this into a React/Next.js/Vite project, add a `package.json`, or
split it into multiple files unless explicitly asked. The single-file
constraint is intentional — it's a portfolio, not an app.

## Positioning — read this before touching any copy

The site's hierarchy, top to bottom, is:

```
Full-Stack Developer
  → builds SaaS & production web applications
  → strong backend + frontend experience
  → specializes in AI integrations and AI-powered features
  → can also handle APIs, payments, automation, deployment
```

Full-stack is the headline identity; AI is the differentiator inside it — not
the other way around. This is a deliberate choice to widen the client pool
while keeping AI as the standout skill. **Do not flip this back to
"AI-first"** (e.g. don't change the hero role line to lead with "AI
Integration Developer") unless explicitly asked to reposition again.

## File structure

```
portfolio.html   ← everything: HTML, CSS (in <style>), JS (in <script>)
AGENTS.md        ← this file
overview.md      ← project/content overview
```

Everything lives in one file, in this order top to bottom:
1. `<style>` — all CSS, using CSS custom properties defined in `:root`
2. `<header class="site">` — sticky nav + mobile menu
3. `<main id="top">` — the 7 sections (see overview.md)
4. `<footer>`
5. `#modalOverlay` — the Featured Work case-study modal (hidden by default)
6. `<script>` — mobile menu toggle, `projects` data object, modal open/close logic

## Design tokens — do not invent new values

All colors, radii, and layout widths are CSS variables in `:root` at the top of
the `<style>` block. **Always reuse these tokens. Never hardcode a new hex color,
a new border-radius, or a new max-width directly in a rule.**

```css
--paper:#FAFAF7        /* page background */
--paper-dim:#F1F0EA    /* subtle section/hover background */
--ink:#14161A          /* primary text / dark surfaces */
--ink-soft:#54565E     /* secondary text */
--ink-faint:#8B8D94    /* tertiary text / labels */
--line:#E3E1D9         /* hairline borders */
--line-strong:#CFCDC3  /* stronger borders, tags */
--signal:#4453F2       /* the one brand accent — links, primary hover, logo dot, role labels */
--signal-dim:#EEF0FD
--accent-a / --accent-a-dim   /* green — LeadScore card, "Full-Stack Development" skill group */
--accent-b / --accent-b-dim   /* amber — AuraPM card, "Backend & Data" skill group */
--accent-c / --accent-c-dim   /* blue (=signal) — FlowDesk card, "AI & Intelligent Systems" skill group */
--radius:6px             /* the only border-radius used on interactive elements */
--maxw:1180px             /* content max-width */
```

If a 4th Featured Work project is added, give it its own accent pair
(`--accent-d` / `--accent-d-dim`) following the existing naming pattern —
don't reuse an existing accent for two different projects.

## Typography — do not swap fonts

- **Display / headings**: `Space Grotesk` (weights 500/600/700)
- **Body / UI text**: `IBM Plex Sans` (weights 400/500/600)
- **Labels, tags, code-like text, role lines**: `IBM Plex Mono` (400/500)

These three are loaded once via Google Fonts in `<head>`. Do not add Inter,
system fonts, or any other typeface. Headings use `h1`–`h4` selectors
globally — don't override font-family per-section.

## UI rules (why the site looks the way it does — keep these intact)

1. **No card-shadow kit.** Cards use hairline `1px solid var(--line)` borders,
   not `box-shadow`. Don't add drop shadows to cards, buttons, or the nav.
2. **One border-radius scale.** `6px` (`var(--radius)`) on buttons/inputs,
   `8–12px` only on the mockup browser-chrome and the CTA block, `100px`
   (pill) only on tag/pill lists. Don't introduce a new radius value.
3. **No ALL-CAPS eyebrow labels.** Section labels use sentence case, not
   `text-transform: uppercase`.
4. **Numbering is used where it's a real ordered list.** `01–04` in "How I
   Work" (a process) and `01–07` running across "Featured Work" and
   "Real-World Experience" (a genuinely numbered project list, matching how
   this content was originally drafted) are legitimate. Don't add numbering
   to "Skills & Tools" — that's grouped, not ordered.
5. **One accent color used for brand/interactive moments.** `--signal` (blue)
   is the only color used for logo dot, links, primary CTA hover, nav-cta
   hover, and role-line text. Per-project accent colors are scoped to their
   own Featured Work card only via `--card-accent`, set on `.work-card.flowdesk`
   / `.leadscore` / `.aurapm`. Don't let a project's accent leak into global
   nav, footer, or CTA styling.
6. **Motion is restrained.** The only animated entrance is the hero load
   sequence (`@keyframes rise`, staggered `animation-delay`). Everything else
   is a hover/click response. Don't add scroll-triggered fade-ins or animate
   every section on load.
7. **Left-aligned, asymmetric layout.** The hero and section heads are
   left-aligned, not centered.
8. **Arrows used once, deliberately.** The `→`-style SVG arrow appears only
   on Featured Work's "View case study" links.
9. **Real-World Experience has no modal, no mockup graphic.** Those four
   entries (AffPilot, Luggage Forward, Test Psycho, First Circle) are
   proof-of-work credits at production companies, not owned products — don't
   invent a UI screenshot or case-study popup for them. Keep them as the
   simpler `.exp-item` rows.

## Responsive breakpoints

- `@media (max-width: 860px)` — nav collapses to hamburger
- `@media (max-width: 820px)` — section padding shrinks
- `@media (max-width: 720px)` — capability/skills grid and product strip go
  to 1 column
- `@media (max-width: 640px)` / `600px` — modal padding, work-card and
  exp-item layouts stack to 1 column

Test any layout change at ~375px (mobile), ~768px (tablet), and ~1280px+
(desktop).

## Content rules — where data actually lives

**Featured Work case studies are not in the HTML.** The three case studies
(role / problem / solution / highlights / stack) live in the `projects`
JavaScript object near the bottom of `<script>`, keyed by `flowdesk`,
`leadscore`, `aurapm`. The modal is populated from this object at click time
via `openModal(key)`.

- Edit the relevant object in `projects`, not the modal HTML skeleton
  (`#modalOverlay` only contains empty placeholder elements like `#mTitle`,
  `#mProblem` — these get filled by JS).
- The short card copy in `.work-card` (numbered tag, title, role-mini,
  one-line description, tech tags, small mockup) is separate and lives
  inline in the HTML — keep it in sync with the modal but shorter.
- `data-project` on each `.work-card` must match a key in `projects` exactly.
- The modal's **Highlights** list and **Stack** list are different things:
  Highlights are capability bullet points ("AI/RAG integration," "Backend
  APIs"), Stack is literal technology names ("Next.js," "PostgreSQL"). Don't
  merge them.

**Real-World Experience content is inline HTML only** (no JS object, no
modal) — each `.exp-item` contains its own title, subtitle, role, description,
and `.exp-tags`. Edit directly in the HTML.

**Do not invent metrics, client names, or testimonials that aren't already
in the file.** There are currently no outcome metrics anywhere on the site —
that's intentional, not an oversight. If asked to "make it more impressive"
or "add social proof," flag that real numbers, logos, or quotes are needed
rather than fabricating specific stats, client names, or testimonials.

## Adding a new Featured Work project (4th case-study card)

1. Add a new key to the `projects` JS object with `tag`, `title`, `role`,
   `problem`, `solution`, `highlights` (array), `tech` (array).
2. Add a new `.work-card` block in `#work` following the existing markup
   pattern exactly (`.work-info` + `.mock` halves), numbered `04 —`, with a
   new class (e.g. `.pipely`) and `data-project="pipely"` matching the JS key.
   Note: `04` is already used by AffPilot in Real-World Experience — if
   numbering both lists as one continuous sequence matters, renumber
   Real-World Experience items to `05–08` instead of reusing `04`.
3. Add a matching CSS rule: `.work-card.pipely{--card-accent:...; --card-accent-dim:...;}`
4. Add a row to `.strip` in the hero linking to the new card's `id`.

## Adding a new Real-World Experience entry

1. Copy an existing `.exp-item` block, update the number, title, subtitle,
   role, description, and `.exp-tags`.
2. No JS or modal changes needed — this section is static HTML only.

## Things an agent should never do to this file

- Add a JS framework, bundler, or `package.json`.
- Add `localStorage`/`sessionStorage`.
- Add tracking/analytics scripts unless asked.
- Replace the custom browser-chrome mockups in Featured Work with `<img>`
  tags pointing at placeholder image services (e.g. `placehold.co`,
  `unsplash`) — if real screenshots aren't available, keep the CSS mockups.
- Add a mockup graphic or "View case study" modal to Real-World Experience
  items — that section is intentionally lighter-weight (see UI rule 9).
- Change the copy tone from plain/direct to salesy ("revolutionary,"
  "cutting-edge," "game-changing," emoji in headings).
- Fabricate outcome metrics, client testimonials, or company logos.
- Flip the positioning back to AI-first without being explicitly asked (see
  "Positioning" above).
