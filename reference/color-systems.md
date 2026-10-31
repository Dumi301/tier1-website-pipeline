# Color Systems — reference

How the workflow builds intentional color systems, plus a bank of ready palettes.
Use this when making the DESIGN DIRECTION color call at spec time, or when
prototyping in an artifact.

## 1. Strategy ladder (restrained → bold)

Pick ONE rung deliberately — don't drift up the ladder mid-build.

- **Mono** — one ink color + one paper/background color, no accent. Use when the
  content (typography, photography, whitespace) IS the design and any color would
  compete with it. Editorial, portfolios, luxury minimal.
- **Single-accent** — mono base + exactly one accent color used sparingly (CTAs,
  links, one highlight per screen). Use when you need one clear action color and
  nothing else should pull the eye. Safest bold move that still reads intentional.
- **Duotone** — two colors carrying roughly equal visual weight (not base+accent,
  but a genuine pair). Use for a graphic, poster-like identity — heritage brands,
  glass/spatial UI, anything that wants a signature two-color mood.
- **Gradient/mesh** — a duotone or triad blended into a continuous field (linear,
  radial, or mesh gradient) rather than flat blocks. Use for soft-club/ambient
  brands, hero backgrounds, glass panels — anywhere you want depth without texture.
- **Full-palette** — 3–5 deliberate colors each with a defined role (bg, ink,
  primary, secondary, tertiary), no color freelancing. Use for structural/
  constructivist or institutional work that needs to encode categories or hierarchy
  in color itself (Bauhaus posters, cultural orgs, editorial sections).
- **Drenched** — the UI is saturated in color rather than color living on a neutral
  base — colored surfaces, colored shadows, colored borders throughout. Use for
  maximalist, Memphis/playful, or culture-drop brands that want to feel loud on
  purpose.
- **Dark-native** — designed FOR a dark surface from the start, not a dark mode
  bolted onto a light system. Use for cyber/dark-tech, gaming, dev-tool, Y2K-chrome
  registers — anywhere dark isn't a fallback, it's the identity.

## 2. OKLCH mechanics

**Why OKLCH over hex/HSL:** perceptual uniformity. Equal numeric steps in
lightness or chroma look like equal visual steps to the human eye. HSL lightness
is not perceptually linear — `hsl(60 100% 50%)` (yellow) reads far lighter than
`hsl(240 100% 50%)` (blue) at the "same" lightness value. OKLCH fixes this, which
is why programmatic ramps built in OKLCH look correct without hand-tuning every
step.

**Building a tint/shade ramp:** hold hue (H) and chroma (C) roughly constant,
step lightness (L) in even increments — e.g. 10 steps from L=97% down to L=15% for
a 50→950 Tailwind-style scale. Nudge chroma down slightly at the extremes (very
light and very dark steps can't hold full chroma without clipping or looking
muddy) — this is the one place you deviate from "constant C" on purpose.

**Tailwind v4** ships its entire default palette as `oklch()` tokens natively — no
plugin needed. Custom palettes should be defined the same way, in `@theme` as
oklch triples, so they compose correctly with the Tailwind color-mix and
opacity utilities.

**Keep chroma realistic** — OKLCH's chroma axis is unbounded but real displays
aren't. Above roughly C=0.25–0.3 (varies by hue) colors start clipping to gamut
edge and stop looking like the OKLCH math predicts. Preview on an actual screen
before committing a high-chroma value.

**Picking a palette that reads intentional, not templated:**
- Commit to ONE signature move (one strategy rung, one accent hue, one gradient
  angle) and repeat it — don't sample from three strategies at once.
- Derive ramps mathematically (step L in OKLCH), not by eye — hand-picked shades
  drift inconsistent and are the fastest way to look "off" without knowing why.
- Test in LIGHT and DARK before finalizing — a palette that only works in one mode
  isn't a system, it's a screenshot.
- **AVOID stock framework colors used unmodified** — Tailwind `blue-500` /
  `indigo-500` / `purple-600` gradient is THE #1 tell of a templated AI site. If a
  color value is copy-pasted from framework defaults with zero adjustment, redo it.
- Ground vivid choices in a real reference (a photograph, a material, a brand
  precedent) rather than inventing a hue in the abstract — it keeps saturated
  choices feeling deliberate instead of arbitrary.

## 3. Light vs dark rules

- **Dark is not inverted light.** Don't just flip background/ink and keep every
  other value — dark mode needs its own contrast, chroma, and elevation decisions.
- **Elevated dark surfaces, not pure #000.** Pure black kills perceived depth and
  crushes shadows/borders. Build dark surfaces as a low-lightness OKLCH step
  (roughly L=12–20%) with a hint of the brand hue, and raise lightness slightly per
  elevation level (card > page bg > modal, etc.).
- **Choose contrast for the dark surface first**, then derive the light surface —
  dark mode is the harder constraint (lower ambient contrast headroom), so solving
  it first prevents retrofitting.
- **Brighten, don't desaturate, accents on dark.** An accent that looked right on a
  light bg often needs higher L (not lower C) to read correctly against a dark
  surface — desaturating makes it look washed out and disconnected from the light-
  mode version of the same brand.
- **"Alpha is a design smell."** Prefer solid computed tokens (a real OKLCH value
  per surface/state) over `rgba()`/opacity layering for elevation or hover states —
  alpha stacks unpredictably over different backgrounds and breaks in dark mode.
  Compute the resulting solid color once and use it as a token.

## 4. The palette bank

Eight named, ready-to-use palettes. Each row states the strategy and primary
use case; dark-native ones are flagged.

### 1. Swiss Paper — mono + single-accent

| Role | HEX | OKLCH |
|---|---|---|
| bg | `#F5F3EF` | `oklch(96.5% 0.006 84.6)` |
| ink | `#111111` | `oklch(17.8% 0 89.9)` |
| accent | `#DA291C` | `oklch(57.5% 0.213 29.6)` |

Strategy: mono + single-accent. When to use: editorial/Swiss/luxury minimal,
portfolios, agencies. Direction fit: **Swiss/Editorial Minimal**.

### 2. Bauhaus Primary — full-palette

| Role | HEX | OKLCH |
|---|---|---|
| bg | `#F2EFE6` | `oklch(95.2% 0.012 91.5)` |
| ink | `#1A1A1A` | `oklch(21.8% 0 89.9)` |
| red | `#D0342C` | `oklch(56.6% 0.194 28.1)` |
| blue | `#1B3F8B` | `oklch(39.0% 0.134 262.8)` |
| yellow | `#F2C230` | `oklch(83.4% 0.158 89.0)` |

Strategy: full-palette. When to use: structural/constructivist editorial,
cultural/institutional. Direction fit: **Structural/Constructivist Editorial**.

### 3. Ink Navy Duotone — duotone

| Role | HEX | OKLCH |
|---|---|---|
| navy | `#0B1D3A` | `oklch(23.4% 0.061 259.5)` |
| cream | `#F4E9D8` | `oklch(93.8% 0.026 78.9)` |

Strategy: duotone. When to use: heritage/ornamental, long-form editorial,
finance-with-warmth. Direction fit: **Luxury Ornamental/Heritage**.

### 4. Quiet Gold — single-accent metallic

| Role | HEX | OKLCH |
|---|---|---|
| bg | `#FAF7F2` | `oklch(97.7% 0.007 80.7)` |
| ink | `#1C1B1A` | `oklch(22.3% 0.002 67.7)` |
| accent (metallic) | `#C9A227` | `oklch(72.8% 0.138 89.7)` |

Strategy: single-accent metallic. When to use: luxury minimal — fashion,
hospitality. Direction fit: **Luxury Ornamental/Heritage** (restrained variant).

### 5. Glass Daylight — duotone accent

| Role | HEX | OKLCH |
|---|---|---|
| ground | `#F0F4F8` | `oklch(96.5% 0.007 247.9)` |
| signal blue | `#2F6FED` | `oklch(57.4% 0.202 262.0)` |
| lilac | `#7C5CFC` | `oklch(59.7% 0.226 286.5)` |

Strategy: duotone accent. When to use: glass/spatial light, SaaS dashboards,
fintech. Direction fit: **Glass/Spatial**.

### 6. Glass Midnight — DARK-NATIVE, duotone

| Role | HEX | OKLCH |
|---|---|---|
| void | `#0B0E14` | `oklch(16.3% 0.014 264.1)` |
| teal glow | `#5EEAD4` | `oklch(85.5% 0.125 181.1)` |
| violet glow | `#8B5CF6` | `oklch(60.6% 0.219 292.7)` |

Strategy: dark-native duotone. When to use: glass/spatial + cyber dark, dev-tool
register. Direction fit: **Glass/Spatial** (dark) / **Cyber/Dark-Tech**.

### 7. Circus Clash — drenched/maximalist clash

| Role | HEX | OKLCH |
|---|---|---|
| magenta | `#FF2E88` | `oklch(66.2% 0.244 1.7)` |
| lime | `#C8FF00` | `oklch(92.8% 0.230 124.0)` |
| cobalt | `#1E3AF0` | `oklch(48.1% 0.266 266.4)` |
| orange | `#FF6B00` | `oklch(70.2% 0.200 45.1)` |
| ink | `#121212` | `oklch(18.2% 0 89.9)` |

Strategy: drenched/maximalist clash. When to use: maximalism, memphis/playful,
culture/drop brands. Direction fit: **Maximalist** / **Memphis/Playful**.

### 8. Chrome & Neon — DARK-NATIVE, drenched triad

| Role | HEX | OKLCH |
|---|---|---|
| void | `#0A0A0F` | `oklch(14.7% 0.011 285.0)` |
| neon green | `#39FF14` | `oklch(87.1% 0.286 141.5)` |
| cyan | `#00E5FF` | `oklch(84.4% 0.146 209.3)` |
| hot magenta | `#FF00C8` | `oklch(67.3% 0.290 341.4)` |

Strategy: dark-native drenched triad. When to use: cyberpunk, Y2K/chrome dark,
gaming/dev-culture. Direction fit: **Cyber/Dark-Tech** / **Y2K/Chrome**.

Unmatched directions from the 11 (Brutalist/Neubrutalist, Retro-Futurism, Soft
Club/Ambient Gradient) don't have a dedicated bank entry — build them from the
strategy ladder directly (Brutalist → mono or full-palette with raw/unrefined
contrast; Retro-Futurism → duotone or gradient/mesh leaning warm/synthwave;
Soft Club/Ambient Gradient → gradient/mesh, low-chroma pastel range).

## 5. Tools

- **Radix Colors** — accessible 12-step light/dark scales, pre-built and
  contrast-tested; good starting ramps when you don't want to derive by hand.
- **Tailwind v4** — native `oklch()` tokens in `@theme`; no plugin required.
- **Coolors** — palette generator with OKLCH export.
- **coolors.xyz** — generates OKLCH ramps exportable straight to Tailwind
  v4/shadcn theme format.
- **Realtime Colors** — preview a palette live on a mock page (nav, hero, buttons)
  before committing.
- **Evil Martians Harmony / apcach** and **Huemint / Polychrom** — OKLCH+APCA
  palette tools for perceptually-tuned, contrast-verified palettes.

Always run every text/background pair through a WCAG contrast check before
shipping — don't trust a "clash" palette (Circus Clash, Chrome & Neon) to be
accessible by default; verify each pairing you actually use.
