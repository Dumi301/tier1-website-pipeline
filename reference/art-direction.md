# Art Direction — reference

Photography sourcing law + treatment consistency. Palette/type/layout live in
`design-directions.md` and `color-systems.md`; this file governs photographic
imagery only.

## How to use

1. This file is sourcing LAW plus treatment-consistency craft for photography
   only — it does not touch palette, type, or layout, those stay in
   `design-directions.md`/`color-systems.md`.
2. The "ship real imagery" mandate and the Unsplash URL sourcing protocol are
   impeccable's job — see `brand.md` §Imagery. This file adds only what's
   missing on top of that mandate, it does not restate it.
3. Non-conflict note: `brand.md` grants "art direction per section" (a full
   visual-world consistency permission). This file's rule is narrower —
   photographic color-grade consistency only, one grade per site. The two
   don't compete.

## Sourcing law (binding)

Rules established in practice, made law. Every sourced photo must clear all five:

1. **No staged/posed stock** — camera-facing models, handshake shots, forced
   smiles. Rule: the demo must not look computer-generated.
2. **No watermarks or stock-site branding** visible in the frame.
3. **No visible faces** unless the business is person-facing AND a specific
   licensed photo of that person exists. No generic stock faces, ever.
4. **No odd-one-out exposure/brightness inside a graded set** — every photo on
   a page reads as one lighting world. Example: a bright/showroom shot was
   rejected against the site's dark-moody grade for exactly this reason.
5. **No visible logos or license plates** in the frame — Re-sourcing
   rule, applies to any third-party mark caught incidentally in a stock shot.

## One-grade-per-site treatment consistency

Exactly ONE grade recipe per site. Pick it once, record it in
`pipeline/art-direction.md`, apply it to every photo — never re-decide the
grade per image. Duotone hex pairs pulled from `color-systems.md`'s palette
bank where a bank entry exists for the direction; the three directions with no
bank entry (marked below) use that direction's own palette values from
`design-directions.md` instead — still zero invented color, just no
dedicated bank row for that cluster.

| Direction | CSS filter recipe | Duotone hex pair (shadow → highlight) | Grain | Notes |
|---|---|---|---|---|
| Swiss / Editorial Minimal | `grayscale(.85) contrast(1.05)` | `#111111` → `#DA291C` (bank: Swiss Paper) | 2% | near-mono base, accent duotone overlay via `mix-blend-mode: multiply`, low opacity |
| Structural / Constructivist Editorial | `grayscale(1) contrast(1.15)` | `#1A1A1A` → `#D0342C` (bank: Bauhaus Primary) | 3% | full B&W base reads as propaganda-poster grade |
| Brutalist / Neubrutalist | `grayscale(1) contrast(1.3) brightness(.95)` | `#000000` → `#FFEE00` (no bank entry — direction's own Raw Brutalist palette) | 5% | harsh, unrefined contrast is the point — don't soften it |
| Maximalist | `saturate(1.4) contrast(1.1)` | `#121212` → `#FF2E88` (bank: Circus Clash) | 3% | push saturation, never desaturate — matches the drenched strategy |
| Memphis / Playful | `saturate(1.2) brightness(1.05)` | `#1E3AF0` → `#C8FF00` (bank: Circus Clash, second pair) | 2% | candy-bright; keep contrast lower than Maximalist's grade |
| Retro-Futurism | `contrast(1.2) saturate(1.3) hue-rotate(-15deg)` | `#0D0221` → `#00F5FF` (no bank entry — direction's own Synthwave palette) | 4% | VHS-adjacent; pairs with the scanline overlay in `motion-library.md` |
| Y2K / Chrome | `contrast(1.05) brightness(1.08)` | `#0A0A0F` → `#FF00C8` (bank: Chrome & Neon) | 2% | glossy and bright; gloss reads via CSS highlight layers, not grain |
| Soft Club / Ambient Gradient | `saturate(.75) brightness(1.05) contrast(.95)` | `#1A1620` → `#D97757` (no bank entry — direction's own palette) | 2% | lowest-contrast grade in the library, washed pastel |
| Glass / Spatial | `grayscale(.4) contrast(1.05)` | `#0B0E14` → `#5EEAD4` (bank: Glass Midnight) | 2% | cool desaturation; glow reads through translucent panels, not photo texture |
| Cyber / Dark-Tech | `grayscale(.9) contrast(1.25) brightness(.85)` | `#0A0A0F` → `#39FF14` (bank: Chrome & Neon, second pair) | 4% | dark near-mono, single neon channel, distinct pick from Y2K's magenta |
| Luxury Ornamental / Heritage | `sepia(.2) contrast(1.05) saturate(.9)` | `#0B1D3A` → `#F4E9D8` (bank: Ink Navy Duotone) | 4% | warm heritage grade, works across Deco/MCM/70s sub-styles alike |

## Crop language

- **Hero:** full-bleed, subject placed for the direction's headline overlay —
  never centered by default.
- **Card thumbnails:** one aspect ratio per card family, consistent across the
  whole family (all service cards same ratio, all team cards same ratio).
- **Default composition:** rule-of-thirds subject placement.
- **Dead-center subject:** banned, except symmetric directions (Luxury
  Ornamental) where centered symmetry is the point.

## Placeholder discipline

When no licensed photo exists for a slot, the placeholder must read as an
intentional imagery slot, not an empty box:

- Direction palette fill + static SVG grain at 2–6% opacity, per that
  direction's grain value above.
- Never a raster placeholder file. Never bare gray or white — Rule:
  placeholders "read as empty, not as imagery."
- Log every substitution in `build-notes.md`.
- Per-direction grain texture notes: see `design-directions.md` §6 and §11 —
  don't restate them here.

## Feeds the ART-DIRECTOR PHASE

These decisions land in `pipeline/art-direction.md`'s photo manifest (sourced
URLs, the one grade recipe, crop notes). The VISUAL CRAFT checker grades
imagery against that manifest, not against this file directly.
