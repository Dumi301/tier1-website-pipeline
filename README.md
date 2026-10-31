# tier1-website-pipeline

Researches a real business and produces ONE paste-ready, fully-unattended Claude Code prompt that builds a classic Tier 1 website (content sites, docs, blogs, basic local-business sites) through a 4-agent plan, build, test, review pipeline. Tier 1 uses no animation libraries and no React: Astro, Tailwind and CSS-only motion (hover transitions, native smooth scroll). The human approval gate is pre-approved in the prompt, so you paste it, walk away, and review the artifacts at the end.

## What you get

```
tier1-website-pipeline/
  SKILL.md                      The skill: protocol, binding rules, full one-shot prompt template
  README.md                     This file
  CHANGELOG.md                  Version history
  reference/
    website-stack.md            Tier definitions, base stack, deploy default
    design-directions.md        11 design directions with tokens
    color-systems.md            Palette and contrast rules
    art-direction.md            Photo sourcing law and placeholder rules
    copy-voice.md               Owner-voice copy register and banned phrases
    motion-library.md           Motion and interaction rules
    page-composition.md         Section archetypes and page rhythm
  agents/
    README.md                   How to install the 4 agents
    dev-planner.md              Turns the brief into an exact spec
    dev-coder.md                Builds exactly what the spec says
    dev-tester.md               Adversarial tests and visual craft checks
    dev-reviewer.md             Read-only APPROVED / REJECTED gate
```

## Requirements
- Claude Code (or another SKILL.md-compatible agent)
- Node 20+
- The impeccable design-craft skill (free, public); the pipeline halts without it
- Context7 MCP (optional, for up-to-date library docs)

## Install
1. Copy this folder to `.claude/skills/tier1-website-pipeline/` (project or `~/.claude/skills/`).
2. Copy `agents/dev-*.md` (the four agent files, not the README) to `.claude/agents/`.
3. Install the impeccable skill.

## Example brief
Paste something like this into Claude Code:

```
Use the tier1-website-pipeline skill.
Business: Maple Street Bakery, 14 Maple St, Springfield
Google Maps: https://maps.google.com/?cid=0000000000
Facebook: https://facebook.com/maplestreetbakery
Language: English. Mobile-first.
Goal: a clean, fast static site with hours, menu and a WhatsApp pre-order link.
No animations needed. No existing site. Prices unpublished: use market-sized placeholders.
Deliver the one-shot prompt, then I will paste it into a fresh session.
```

## What the output looks like
The skill replies with the tier confirmation, the research brief (unverified items flagged) and one large prompt. Running that prompt produces a `pipeline/` folder:
- `spec.md` (the build spec), `ownership.md` (file ownership map)
- `build-notes.md` (assumptions, deviations, component swaps)
- `test-report.md` (build, CTA, responsive, token and visual-craft evidence)
- `design-review/` (screenshot matrix), `craft-rules.md`, `art-direction.md`
- `audit-log.md` (single scoped audit), `review-verdict.md` (punch-list)
plus the built site with favicon, OG image, custom 404 and theme-color.

## Limitations
- No deployment performed for you, and no backend (booking, payments, CMS are out of scope).
- Prices, reviews, photos and unverified names ship as clearly marked placeholders you must replace.
- Needs the impeccable skill and a capable model; a full run is the fastest of the three tiers (well under 30 minutes).
- Tier 1 is deliberately static: no animation libraries, no registry components, no React islands. For animated marketing sites use tier2-website-pipeline.


## License
Single-buyer, non-exclusive license. No redistribution or resale.

## Install

Clone or download this repo, then copy the folder into `~/.claude/skills/tier1-website-pipeline/` (and `agents/*.md` into `~/.claude/agents/`). Also listed free on Agensi: https://agensi.io/skills/fast-static-astro-website-from-a-business-brief

## Paid tiers (same protocol, more output)

- **Animated marketing site** (React islands, registry animations, design-craft grader) — https://agensi.io/skills/animated-marketing-website-from-a-business-brief-astro ($19)
- **Scroll-driven 3D site** (GSAP ScrollTrigger + React Three Fiber, storyboard-bound) — https://agensi.io/skills/scroll-driven-3d-website-from-a-business-brief-r3f ($29)
- **4-agent feature pipeline** for any feature, not just sites — https://agensi.io/skills/plan-build-test-review-4-agent-feature-pipeline ($9)

## License

MIT — see `LICENSE`.
