---
name: website-stack
description: Standard stack and design-resource protocol for building ANY website or web frontend. Use whenever the task involves creating, redesigning, or scaffolding a website, landing page, portfolio, web app UI, or marketing site — including when the user just says "make me a site/page". Defines the base install, when to add the animation/3D layer, and which component registries and reference sources to pull from before writing custom UI code.
---

# Website Stack Protocol

## Step 0 — Classify the project before installing anything
Ask (or infer from the request) which tier this is:
- **Tier 1 — Classic/simple:** content site, blog, docs, basic business site. No animation libraries. Base stack only.
- **Tier 2 — Polished/marketing:** landing pages, portfolios, product sites that should feel "expensive". Base stack + motion + component registries.
- **Tier 3 — Immersive:** 3D elements, scroll-driven scenes, hero WebGL. Everything in Tier 2 + GSAP + R3F.

Never install Tier 2/3 dependencies for a Tier 1 site. Never hand-write animation code when a registry component exists (Tier 2 rule below).

## Step 0.5 — Pick a Design Direction
The `reference/` files below ship with this package (same folder).

Tier (1/2/3) governs complexity and motion budget only — it never decides the
LOOK. Pick ONE of the 11 directions in `reference/design-directions.md` (default:
Swiss/Editorial Minimal) for every project, at every tier. Load all six
reference files — `reference/design-directions.md`, `reference/color-systems.md`,
`reference/motion-library.md`, `reference/art-direction.md`,
`reference/page-composition.md`, `reference/copy-voice.md` — every one of them,
always present in this skill bundle, never "load if present" — and inject the
chosen direction's recipe (palette hex+OKLCH, type pairing, layout pattern,
motion vocabulary filtered to the tier's budget) into the build spec's DESIGN
DIRECTION block. State the direction + one-line justification right after the
tier line.

## Base stack (every tier)
Astro (static output) + Tailwind CSS v4, CSS-first.
```bash
npm create astro@latest <name> -- --template minimal --typescript strict
cd <name>
npm install tailwindcss @tailwindcss/vite
npx astro add react
```
- **Tailwind v4, CSS-first** via the `@tailwindcss/vite` plugin — NOT `@astrojs/tailwind`. Register it in `astro.config.mjs` (`vite: { plugins: [tailwindcss()] }`) and pull it in with `@import "tailwindcss";` from your global stylesheet. Theme tokens live in CSS via `@theme`, not a `tailwind.config.js`-first setup.
- **Fonts:** self-hosted with `@fontsource/<font>` — never runtime Google Fonts.
- **Images:** `astro:assets` (`<Image />` / `getImage()`) for local art — no raw `<img>`.
- **JavaScript is external** — ship JS as modules Astro processes; no inline `<script>` blobs.
- **React only as islands** (`@astrojs/react`): use React solely for registry components that need it, mounted as islands — `client:visible` by default; Tier 3 hero scenes use `client:load`.
- **Next.js is no longer the base.** Permitted ONLY if a future app-like project (auth, server routes, a real dashboard) explicitly flags the need — a static marketing/portfolio/landing site never does.

## Theme (every tier)
Default shadcn colors/fonts are forbidden as a final deliverable. The chosen
Design Direction's palette (hex+OKLCH from `reference/design-directions.md` /
`reference/color-systems.md`, picked in Step 0.5) is the PRIMARY source of truth
for theme tokens — paste its CSS variables into globals.css and tell the user
which direction/palette was applied and why.
- Optional starting scaffold only: tweakcn (https://tweakcn.com) — if a
  direction's palette needs shadcn variables as a base, `npx shadcn@latest add
  <tweakcn-theme-url>` can seed the variable structure, then overwrite the values
  with the direction's palette. Never let a tweakcn theme's own colors ship as
  final — the Design Direction palette always wins.

## Tier 2 additions — motion + components
```bash
npm install motion
```
Component sources, in priority order. ALWAYS check these before writing custom UI/animation code:
1. **React Bits** (https://reactbits.dev) — primary. Animated backgrounds, text effects, interactive bits. Install per component: `npx shadcn@latest add https://reactbits.dev/r/<Component>-JS-TW`. Verify each component's peer deps on its registry page before speccing: **Silk** is three/@react-three/fiber-based (~855 KB shipped) — never spec it as a primary decorative background; **Aurora/Iridescence** are ogl (~10 KB).
2. **Aceternity UI** (https://ui.aceternity.com) — hero sections, cards, backgrounds, premium-feel animated components. Install per component: `npx shadcn@latest add <component-url from their docs>`
3. **Magic UI** (https://magicui.design) — marquees, shimmer buttons, blur fades, number tickers. Same shadcn add pattern.
4. **Motion Primitives** (https://motion-primitives.com) — MIT, motion+Tailwind text/micro-interaction primitives (runs on the `motion` already in the stack). Same shadcn add pattern.
5. **Fancy Components** (https://fancycomponents.dev) — free, quirky text/physics microinteractions. Same shadcn add pattern.
6. **SmoothUI** (https://smoothui.dev) — ~130 free components, official shadcn registry: `npx shadcn@latest add @smoothui/<Component>`.
7. **21st.dev** (https://21st.dev) — community search when the above don't have what's needed. Spline 3D embeds surfaced here are BANNED on client work (free tier watermarks web exports + needs GUI work per scene). Same shadcn add pattern.
8. **Kokonut UI** (https://kokonutui.com) — free, 100+ Tailwind/shadcn/Motion-based animated components. Same shadcn add pattern.
9. **Watermelon UI** (https://registry.watermelon.sh) — structured marketing BLOCKS only (pricing/feature grids); redundant elsewhere. Same shadcn add pattern.

Rule: pulling an existing component and restyling it beats writing animation code from scratch. Only write custom motion code when no registry component fits.

Docs freshness: if the Context7 MCP is installed ("use context7"), verify registry peer deps and current library APIs (Astro, Tailwind v4, motion/ogl/gsap/R3F) through it instead of trained memory; absent, verify via WebFetch of the registry/docs page.

## Tier 3 additions — GSAP + 3D
```bash
npm install gsap @gsap/react three @react-three/fiber @react-three/drei lenis
```
- GSAP is fully free including ScrollTrigger, SplitText, MorphSVG. Use `useGSAP()` from @gsap/react for React-safe cleanup.
- **3D assets CC0-first:** Poly Haven (models + HDRIs), Quaternius, Kenney, KayKit — no attribution, resale-safe. Sketchfab / Poly Pizza only with a per-asset license check logged in build-notes.md. Load .glb via drei's `useGLTF()` (or gltfjsx-generated components); Poly Haven HDRI through drei `<Environment>` is the default cheap premium-lighting move.
- **Smooth scroll:** Lenis (`lenis` pkg + `lenis/react`, ~3 KB) is the standard ScrollTrigger pairing. The old `@studio-freight/lenis` package is dead.
- **Optional, per-storyboard only:** `@react-three/rapier` physics (log WASM weight), shadergradient (`@shadergradient/react` — renderer pkg, needs R3F).
- **Out for unattended builds:** Spline (free-tier watermark on client deliverables + GUI work per scene) and Theatre.js (editor-driven — operator-authored showcases only).
- Scroll-driven 3D pattern: GSAP ScrollTrigger drives R3F state (camera position, scene progress) — do not fight R3F's frame loop with per-frame GSAP tweens on the canvas.

## Design reference (all tiers, before layout decisions)
- **Mobbin** (https://mobbin.com) — real production app/site screens. When the user is unsure about layout or flow, direct them to check Mobbin for how top products solve the same screen, or ask them to describe/screenshot a reference from it. Do not invent novel layouts for standard patterns (pricing pages, onboarding, dashboards) — copy proven structure.

## Output rules
- State which tier was chosen and why, in one line, before scaffolding.
- List every registry component pulled and its source.
- If the user asks for something "simple" but requests animated components, flag the contradiction instead of silently upgrading tiers.

## Post-review binding rules (from a shipped-site review — binding on every spec and build)
1. **DEPLOY DEFAULT — Cloudflare Pages.** Deploy with `npx wrangler pages deploy dist --project-name <name>` — the `--project-name` flag is mandatory (omitting it can hit a preview branch while the live URL silently never updates). Unsigned-client pitch demos ship a `public/_headers` file with `X-Robots-Tag: noindex` until the client signs. Auth = `npx wrangler login` in a plain terminal; never handle secrets non-interactively.
2. **PEER DEPS PER COMPONENT.** Verify each registry component's actual dependencies on its registry page at spec time — do not assume by category. Known: React Bits **Silk** is three/@react-three/fiber-based (~855 KB shipped) — never spec it as a primary decorative background; **Aurora/Iridescence** are ogl (~10 KB); **Paper Shaders** (`@paper-design/shaders-react` — Apache-2.0, zero-dep animated WebGL backgrounds) is pre-1.0 with explicit breaking-change warnings → ALWAYS pin the exact version in the spec and verify the current API via Context7. Lenis installs as `lenis` (the old `@studio-freight/lenis` is dead).
3. **DECORATIVE JS BUDGET (binding in every spec).** Purely decorative elements (hero backgrounds, ambient effects) ≤ 60 KB shipped JS. Over budget → ogl alternative or static gradient. Decided at spec time, never a mid-run judgment call.
4. **HYDRATION VISIBILITY (binding).** Animate-in content must SSR VISIBLE; the island applies the initial hidden state via JS at hydration, immediately before animating. `<noscript>` rescue covers JS-off only — it does not cover the JS-enabled-but-not-yet-hydrated window, and an invisible LCP element there is a real defect.
5. **REGISTRY-EDIT SCOPE.** The no-edit rule restricts ANIMATION behavior (easing, duration, stagger, motion structure). Non-behavioral edits required to satisfy other binding checks (SSR guards, dead remote-asset literals, lang-consistent aria strings) are pre-authorized — one log line each in build-notes.md.
6. **TEXT FLOOR.** No BODY text under 14px at 375px; decorative labels (nav links, eyebrows, badges) floor 12px. Never write a flat sub-14px ban alongside text-xs mandates.
7. **CONTACT IDENTITY.** All business identity (email, phone, WhatsApp number, address, hours, name) lives in ONE file — `src/data/business.ts` — and every consumer imports from it (scripts that cannot import read a data-attribute rendered from it). Grep-proof in DONE WHEN: identity literals appear in exactly one file.
8. **TIER 2 REGISTRY ORDER.** React Bits primary, Aceternity UI / Magic UI fallback, then Motion Primitives / Fancy Components / SmoothUI, then 21st.dev (Spline embeds banned on client work) / Kokonut UI / Watermelon UI (marketing blocks only) — matches the claude.ai-side tier skills.
