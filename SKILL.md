---
name: tier1-website-pipeline
description: "Researches a real business and generates ONE fully-unattended, paste-ready Claude Code prompt that builds a classic Tier 1 website (content sites, blogs, docs, basic local-business sites; NO animation libraries, CSS-only motion) through a 4-agent plan, build, test, review pipeline with the human gate pre-approved. Use when a user wants a tier 1, simple or basic website, says 'just a clean site for this business', or supplies business links and describes a static, no-frills build. If the user says 'simple' but describes animated components, flag the contradiction and point to the tier2-website-pipeline skill instead of silently upgrading."
---

# Tier 1 Website — research → one-shot unattended prompt

## Requirements
- The **impeccable** design-craft skill (free, public) must be installed; the pipeline halts without it.
- Claude Code (or any SKILL.md-compatible agent) with the bundled `agents/` installed into `.claude/agents/` (see `agents/README.md`).

## Division of labor (never violate)
- This skill runs inside Claude Code (or any SKILL.md-compatible agent). The bundled
  `agents/` (dev-planner, dev-coder, dev-tester, dev-reviewer) and `reference/`
  (website-stack, design directions, color, copy, motion, page composition) are part
  of this package.
- Its job: classify the tier, run the business research (inline checklist below), and
  produce ONE big paste-ready prompt. The prompt is then executed by the dev-team
  pipeline plus `reference/website-stack.md`. Never pretend to scaffold/install while
  writing the prompt. The deliverable here is the prompt.
- `reference/website-stack.md` owns tier definitions and the base stack; don't duplicate.

## Protocol (in order)

### 1 — Confirm tier (one line, always first)
State "TIER 1 — classic/simple" + one-line justification. Tier 1 means NO animation
libraries, no React, no registry components. CSS-only transitions (hover states,
smooth scroll) are fine. If the user describes registry animations or 3D → flag and point to
tier-2 / tier-3 sibling skills.

### 2 — Research the business (full brief, every time)
Inline research checklist (all items, every time):
1. Maps listing found; confirm name, category, address, rating, review count.
2. Existing-site check: does a real site load? Is it broken, dated, or absent?
3. Hours, phone, address, services — from the listing, the business's social pages,
   and local business directories plus the national company register for your market
   (for the legal entity).
4. Reviews: verbatim, sourced quotes only, or marked placeholders (rules below).
5. Three comparable local businesses (same area), used to size placeholder prices.
Use deep research across Google Maps, Facebook, and local directories.
Data honesty rules (non-negotiable):
- Reviews: only verbatim, sourced quotes; if unverifiable, placeholders marked
  `// FAKE-REPLACE`. Never borrow from similarly-named businesses.
- Prices: unpublished → market-sized "from $X / from €X" placeholders marked
  `// CONFIRM-PRICE`, comparables cited.
- Unverified names → `[CONFIRM NAME]`; conflicting ratings → soft claim +
  `[CONFIRM REVIEW COUNT]`.
- Flag every unverified item explicitly.

### 3 — No external design-tool step at Tier 1
The visual direction lives entirely in the spec's tokens (palette, font pairing,
spacing rules). If the user wants a design-tool mockup anyway, treat it as an upgrade
signal — ask if this is really Tier 2.

### 4 — Generate the one-shot prompt
Fill the template below from the research brief. BUILD STEPS stay concrete
(sections, content, data files) even without animation components.

## Tier 1 stack facts
- Astro + Tailwind v4 CSS-first via `@tailwindcss/vite` (NOT the deprecated
  `@astrojs/tailwind`), static output. NO @astrojs/react, NO motion/gsap/ogl, NO
  registry components. Zero client-side JS is the ideal; small vanilla external JS
  files only where needed (mobile nav toggle, form handling).
- Self-hosted fonts via @fontsource (no Google CDN). Images through astro:assets.
  All JS external. Cloudflare Pages later — deployment OUT OF SCOPE for the run.
- DESIGN DIRECTION (authoritative, Tier 1's equivalent of the tier-2/3 block; the
  spec's tokens are the sole visual source of truth): DIRECTION [chosen direction
  name from design-directions.md + signature traits]; PALETTE [the chosen
  direction's named palette from color-systems.md — hex + OKLCH + roles + contrast
  ratios, one accent color]; TYPOGRAPHY [the chosen direction's font pairing from
  design-directions.md via @fontsource — serif display + sans body still works at
  Tier 1]; STYLE generous whitespace, a11y contrast checked, mobile-first —
  local-business traffic is mobile Maps/Instagram clicks; MOTION [the direction's
  motion vocabulary from motion-library.md, filtered to Tier 1's CSS-only budget —
  hover transitions, native smooth-scroll, clamp() fluid type]; IMAGERY [photo
  manifest + grade recipe per pipeline/art-direction.md]; COPY VOICE [owner-voice
  keynote facts per pipeline/art-direction.md].
- Zero-JS texture allowed: Pattern.css (CSS-only background patterns) or static
  SVG backgrounds from a pre-generated asset library (Haikei/fffuel exports,
  added as plain assets). css-doodle is NOT Tier 1 (it's a JS web component —
  that's Tier 2 territory).
- No-backend booking pattern (same as Tier 2): client-side form → URL-encoded
  WhatsApp deep link (`https://wa.me/<number>?text=...`, newlines %0A, diacritics
  encoded) + tel: button + hours. Backends OUT OF SCOPE for v1.
- SEO basics always: local-intent meta title/description, OG tags + og-image,
  @astrojs/sitemap, correct `lang`, per-page unique titles.

## The prompt template (fill slots, deliver as one block)

```
Use the dev-team skill and website-stack skill. Run the full dev-team pipeline
(dev-planner → dev-coder → dev-tester → dev-reviewer) on the spec below.

PIPELINE CONTRACT (non-negotiable):
- Write artifacts to pipeline/: spec.md, build-notes.md, test-report.md,
  review-verdict.md.
- AUTONOMY — FULLY UNATTENDED RUN. The embedded spec below IS the approved spec: I am
  approving it now, in advance, by giving you this prompt. dev-planner writes
  pipeline/spec.md as a FAITHFUL expansion (no scope additions), then proceed straight
  to dev-coder — the human gate is satisfied by this pre-approval. Material deviations
  are logged in build-notes.md, not built.
- NO MID-RUN QUESTIONS. Instead of questions.md: make the most conservative reasonable
  assumption, log it in build-notes.md under ASSUMPTIONS-MADE, continue.
- Max 2 rejection loops: after a 2nd dev-reviewer rejection, HALT and write
  pipeline/failure-report.md. A clean halt with a report is the correct unattended
  failure mode.
- Maps onto PLAN → WORK → VERIFY → GATE with the gate pre-satisfied.

DESIGN CRAFT (binding — the anti-slop layer; a run without it produced generic
AI output that no agent ever rendered or looked at):
- BEFORE Phase 1, the orchestrator loads the `impeccable` skill. If
  `impeccable` is missing or fails to load: HALT with
  pipeline/failure-report.md — never build on default taste. A Tier 1 site
  lives or dies on type scale, spacing rhythm, and color restraint; craft
  matters MORE here, not less, because there is no animation to hide behind.
- Load the website-stack reference files (always present in this skill
  bundle, not optional): `reference/design-directions.md` (the chosen
  direction's full recipe), `reference/color-systems.md` (palette + OKLCH
  strategy), `reference/motion-library.md` (motion recipes; obey THIS
  tier's motion budget — T1 CSS-only, T2 Motion+optional Lenis/GSAP ≤60KB
  decorative JS, T3 full GSAP/R3F/shader), `reference/art-direction.md`
  (photo sourcing law + one-grade-per-site treatment consistency),
  `reference/page-composition.md` (section-archetype menu + adjacency/
  repetition caps), `reference/copy-voice.md` (owner-voice register +
  specificity-from-research rule).
- Distill its craft rules ONCE into pipeline/craft-rules.md; worker prompts
  POINT to that file (token economy). Craft rules bind all visual output
  alongside the spec's design tokens.
- PHASE 2 gains a mandatory 6th checker — VISUAL CRAFT: install playwright
  chromium (devDependency only), build + `astro preview`, screenshot EVERY
  route at 375/768/1440, saved to pipeline/design-review/. This checker —
  and ONLY this checker, the sole exception to the image-read ban — VIEWS
  its own screenshots and grades each page against craft-rules.md AND
  pipeline/art-direction.md: PASS or SLOP per page with one-line reasons in
  test-report.md (type scale, spacing rhythm, accent restraint, hierarchy,
  imagery quality, imagery grade consistency, section-rhythm variety
  (archetype map followed), interaction-state completeness (hover/active/
  focus-visible), brand-finish artifacts present). Any SLOP grade is a
  reviewer-blocking defect routed back to the owning worker.

PARALLEL EXECUTION — SPEED IS THE PRIORITY (non-negotiable):
- PHASE 0 (serial, one agent, short): scaffold, npm installs, @theme tokens,
  BaseLayout, global.css, src/data/* files, Nav/Footer. These SHARED files are FROZEN
  after Phase 0 — no parallel worker edits them.
- PHASE 0.5 (ART DIRECTION — lightweight, may be folded into the Phase 0
  agent as its final step, output file still mandatory): reads the research
  brief + chosen direction + art-direction.md/page-composition.md/
  copy-voice.md; writes BINDING pipeline/art-direction.md: (1) photo
  manifest — exact sourced URLs passing the sourcing law, ONE grade recipe
  for the whole set, crop notes; (2) per-page section-archetype map obeying
  the adjacency/repetition caps; (3) the page's ONE oversized signature
  element; (4) copy-voice keynote — 3–5 research facts that MUST appear.
  Builders may not deviate without a logged build-notes.md entry.
- PHASE 1 (BUILD — mandatory fan-out): dev-coder acts as build-orchestrator and
  spawns parallel subagent builders via the Task tool. FLOOR: 5 concurrent workers;
  CEILING: 20; one worker per page, plus one for SEO/OG/sitemap, plus one for the
  assets/image pipeline.
- FILE-OWNERSHIP MAP: before fan-out, orchestrator writes pipeline/ownership.md
  assigning every worker an EXCLUSIVE file list. No two workers touch the same path;
  needed shared-file changes are logged, then applied serially by the orchestrator
  after the wave.
- PHASE 2 (TEST — parallel): dev-tester fans out ≥6 checkers (build+routes,
  CTA/WhatsApp decode, perf/assets + no-framework bundle check, responsive
  375/768/1440, content/marker audit, VISUAL CRAFT per the DESIGN CRAFT
  block), merged into one test-report.md.
- Review stays single-agent; rejection fixes route back to each file's original
  owner, in parallel where independent.

LIVE AUDITOR (independent watcher — single checkpoint, scoped):
- Spawn ONE audit subagent via the Task tool, model strongest available model, READ-ONLY
  (writes only pipeline/audit-log.md), invoked EXACTLY ONCE: after Phase 2
  (test) completes, before dev-reviewer starts. No per-phase checkpoints —
  a prior run measured 4 checkpoints at ~16% of total tokens and ~5 min of
  blocking tails, all PASS; one late audit catches the same defect classes.
- SCOPED INPUTS ONLY (token discipline): pipeline/ artifacts (spec.md,
  build-notes.md, ownership.md, test-report.md), git log/status, targeted
  greps for honesty markers, and file LISTINGS. It must NOT read the full
  source tree, must NEVER read image/binary files, and must NOT re-run builds.
- It audits: ownership.md compliance vs git history, spec drift, data-honesty
  markers present, decorative JS budget number from test evidence, test
  evidence being real output rather than descriptions, and CRAFT COMPLIANCE:
  pipeline/craft-rules.md exists, pipeline/design-review/ screenshots exist
  (verified via ls only — the auditor never views them), and every page has
  a PASS/SLOP grade in test-report.md.
- Output: PASS/FLAG per check, one-line reasons, in audit-log.md. dev-reviewer
  MUST read it and address every FLAG (fixed / accepted-with-reason).
- The two mid-run HALT conditions are STANDING RULES enforced by the
  orchestrator at wave merges (not by auditor invocations): (a) fabricated
  data presented as real, (b) a worker edited a frozen/shared or non-owned
  file → halt with pipeline/failure-report.md.
TOKEN & CONTEXT ECONOMY (binding — tokens are wall-clock: a prior run's
2.2M-token appetite tripped a session usage limit and stalled 4+ hours):
- Whole-run token target: under ~1M. Parallel fan-out stays (measured 3-4×
  speed-ups); the waste is context, not concurrency.
- NO agent reads image/binary files into context, ever — SOLE EXCEPTION: the
  VISUAL CRAFT checker views the screenshots it captured, nothing else.
  Everyone else verifies assets via ls/file sizes/build output. (Prior run:
  ~1.4M chars of PNGs as base64.)
- Orchestrator economy: worker prompts POINT to pipeline/spec.md sections by
  name instead of restating them; wave results read via report files and
  tails, not full transcripts; own commentary terse.
- Workers receive only their owned file list + the spec sections they need.
- git init in Phase 0; commit at every phase boundary ("checkpoint: <phase>").
- Phase 0 stays MINIMAL (scaffold, deps, tokens, layout shell, git init);
  data files, asset/photo intake, Nav/Footer become owned Phase-1 work units.
  (Prior run: 12.5 serial Phase-0 minutes, second-longest pole.)
- Asset emission: never eager-glob original images (import.meta.glob eager on
  raw photos shipped 25 MB of source PNGs into dist/ in a prior run). Import
  via astro:assets only; self-check pastes dist/ total size and flags
  originals appearing in it.

STACK: [Astro + Tailwind v4 static block above, project subfolder name]

TIER: TIER 1 — classic/simple. NO animation libraries, NO React, NO registry
components. CSS-only transitions permitted. Do not add motion because it "would look
nicer" — that is a spec deviation to log, not build.

================= EMBEDDED SPEC =================
GOAL / TIER / FILES / BUILD STEPS / EDGE CASES / OUT OF SCOPE / ASSUMPTIONS / DONE WHEN
- GOAL: [business, language, mobile-first, single conversion goal, booking pattern]
- FILES: [indicative tree: layouts, static components, pages, src/data/ files, assets]
- BUILD STEPS: [numbered; sections + content per page; reservation form → WhatsApp
  template with real phone number; SEO block; hours/map/contact]
- EDGE CASES: [every FAKE-REPLACE / CONFIRM marker from research; WhatsApp URL
  encoding; responsive at 375px]
- OUT OF SCOPE: [animation libraries and React entirely; backend/booking/payments/CMS;
  deployment; real photos/prices/reviews]
- ASSUMPTIONS: [verified contact facts; placeholder image sourcing]
- DONE WHEN: [pages build+render; CTAs work; zero client frameworks shipped; every
  page graded PASS by the VISUAL CRAFT checker (no unresolved SLOP); brand-finish
  artifacts present (favicon, OG image, custom 404, theme-color meta); nothing
  fabricated presented as real]

================= ONE-SHOT + SELF-CHECK (paste evidence, not descriptions) ===========
1. `npm run build` — paste output tail; failure = fix and rerun.
2. List all routes rendered.
3. Verify every CTA: nav, tel:, WhatsApp — paste the generated wa.me URL and DECODE it
   to prove text/newlines/diacritics.
4. Perf: astro:assets image manifest + sizes, lazy below-fold, no Google Fonts CDN,
   fonts from _astro/fonts. Confirm NO react/motion/gsap in the dependency tree or
   dist/ bundles — paste the check.
5. Responsive at 375/768/1440 — note overflow.
6. Craft evidence: confirm pipeline/design-review/ holds the full screenshot
   matrix and paste the per-page PASS/SLOP table from test-report.md.
7. Brand-finish check: confirm favicon/OG/404/theme-color present in dist/ output —
   paste the file listing.
8. PUNCH-LIST in review-verdict.md — no silent issues.
```

## After the run (tell the user this)
Read in order: **build-notes.md** (ASSUMPTIONS-MADE + deviations — this replaced the
gate) → **test-report.md** (evidence) → **review-verdict.md** (punch-list). Owner
supplies real prices/reviews/photos later.

## Standing rules
- The DESIGN CRAFT block ships VERBATIM in every generated prompt — a prompt
  without it is an incomplete delivery. (Prior failure: no craft layer, no
  visual checker → generic AI output shipped and nobody ever rendered a page.)
- Unattended default; the trade is review-at-the-end — say so once at delivery.
- Speed target: Tier 1 is the fastest tier — well under 30 min with the swarm; serial
  floor is Phase 0 + final build. The parallel contract (frozen shared files +
  ownership map, one swarm per repo) also lets an operator run many sites concurrently.
- Full research even at Tier 1: a simple site built on guesses is still decoration.
- Every delivery ends with the next action: `cd` into your demos folder → paste → leave.
- If the user starts rebuilding tooling instead of running the prompt, call it out.
