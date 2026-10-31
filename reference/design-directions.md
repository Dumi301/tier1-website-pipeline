# Design Direction Library

A menu of web-buildable aesthetic directions, distilled from a "50 Design Styles"
survey down to 11 buildable clusters. This file is the LOOK layer of a site spec.

## How to use

1. Build **TIER** (Tier 1 static / Tier 2 marketing+motion / Tier 3 immersive) is
   COMPLEXITY. This file is the LOOK, chosen orthogonally — tier and direction are
   two independent decisions, not one axis.
2. A direction is picked at EVERY tier. The tier governs the motion budget and
   build complexity, NOT whether a look applies. A bold direction at Tier 1 still
   sets color, type, and layout — it just gets CSS-only motion instead of
   GSAP/R3F. There is no "no direction" default.
3. Pick ONE direction per project. Don't blend two recipes — a diluted mix reads
   as templated, which is the exact failure mode this library exists to prevent.
4. The chosen direction's recipe gets injected verbatim into the build spec's
   DESIGN DIRECTION block (palette hex+OKLCH, type pairing, layout pattern, motion
   vocabulary) — that block is the sole visual source of truth downstream, per
   `website-stack`'s binding spec rules.

## Triage — all 50 styles from the source reel

BUILD = translates to a full site system. ADAPT = accent/section treatment only,
needs a stable base to sit inside. SKIP = a poster/illustration/print idiom with
no layout grammar — honest about the boundary, not everything decorative is a
website direction.

| Style | Tag | Reason |
|---|---|---|
| Swiss | BUILD | grid + type system IS a layout system; direct site translation |
| Modernism | BUILD | functionalist grid/whitespace logic maps directly to page structure |
| Minimalism | BUILD | reduction-to-essentials is a full layout philosophy, not a decoration |
| Luxury Minimal | BUILD | minimalism + premium type/spacing, a distinct full-site register |
| 80's Editorial | BUILD | magazine grid + big type hierarchy translates to web layout wholesale |
| Vector Minimalism | BUILD | flat geometric-illustration logic scales to a full component system |
| Brutalism | BUILD | raw-HTML aesthetic is inherently a build system, cheapest to ship |
| Neubrutalism | BUILD | bordered/offset-shadow component language, now mainstream product UI |
| Y2K | BUILD | gloss/chrome/bubble language extends across nav, buttons, cards coherently |
| Glassmorphism | BUILD | translucent-panel material is a complete UI system, proven at scale |
| Cyberpunk | BUILD | dark neon-HUD language covers nav/hero/cards/type as one system |
| Cyberminimalism | BUILD | dark + signal-color restraint, a disciplined full-site register |
| Tech Spec | BUILD | schematic/data-label system maps to docs, dashboards, product sites |
| Maximalism | BUILD | collage/bento/clash logic is a complete (if loud) layout system |
| Blueprint | BUILD | linework/annotation system extends across full information architecture |
| Bauhaus | ADAPT | geometric primitives + primary triad read best as section accents, not a full skin |
| Constructivism | ADAPT | diagonal/propaganda-poster composition is a strong hero move, exhausting sustained |
| Art Deco | ADAPT | ornamental motifs (sunburst, fan, chevron) frame content, aren't a component system |
| Deconstructivism | ADAPT | intentional grid-breaking needs a stable grid to break against |
| Post-Modernism | ADAPT | collage-of-references works section by section, incoherent as a whole-site rule |
| New Wave | ADAPT | expressive graphic-poster typography as hero treatment, too loud sustained |
| Mid-Century Modern | ADAPT | organic shapes + warm palette give brand mood, thin as a full layout system |
| 70's Retro | ADAPT | earthy palette + groovy dividers work as texture, not structural logic |
| Experimental Type | ADAPT | belongs on headlines/hero words, unreadable at body-copy scale |
| Synthwave | ADAPT | neon-grid-horizon is a hero/section set-piece; whole-site fatigue risk |
| Vaporwave | ADAPT | nostalgia-mood palette and motif, thin as a functional component system |
| Memphis | ADAPT | squiggle/confetti decoration layered onto a real grid, not a grid substitute |
| Kidcore | ADAPT | candy-bright playful accents, not a full information-hierarchy system |
| Type Doodles | ADAPT | hand-drawn marks work as annotation/CTA accents only |
| Naive | ADAPT | illustration-forward warmth is a section mood, not a layout system |
| Glitch | ADAPT | a motion/texture accent (folds into Maximalist and Cyber directions here) |
| Acid | ADAPT | high-chroma palette/texture accent, folds into Maximalism |
| Chromecore | ADAPT | metallic-surface treatment for specific elements, not full pages |
| Web 2.0 Gloss | ADAPT | bevel/gloss button language, a component treatment inside Y2K |
| Bubbleglam | ADAPT | candy-plastic surface treatment, folds into Y2K/Chrome |
| Cyberpop | ADAPT | neon-pop color accent, folds into Y2K/Chrome or Cyber depending on tone |
| Neumorphism | ADAPT | soft-UI shadow language for specific controls; full-site version has known a11y issues |
| Skeuomorphism | ADAPT | literal-material textures for isolated elements (icons, toggles), not a page system |
| Gen X Soft Club | ADAPT | ambient-gradient mood/texture; needs a disciplined layout around it (see cluster 8) |
| Surveillance | ADAPT | CCTV/HUD-overlay texture and mood, folds into Cyber/Dark-Tech as accent |
| Web 1.0 | ADAPT | nostalgia/novelty texture (tables, marquee, guestbook), unusable as a real production layout |
| Art Nouveau | SKIP | organic ornamental illustration style (Mucha-era linework), not a layout grammar |
| Grunge | SKIP | a texture/photo-treatment idiom (distressed, torn paper), not a structural system |
| Punk | SKIP | collage/zine poster idiom (xerox, cut-and-paste), belongs on one asset, not a page |
| Pop Art | SKIP | illustration/print idiom (halftone, Lichtenstein dots), a texture not a grid |
| Italo Disco | SKIP | album-cover/poster mood board, no layout vocabulary of its own |
| Gothic | SKIP | ornamental/blackletter type + illustration mood, not a component system |
| Steampunk | SKIP | prop/illustration aesthetic (brass, gears, Victorian machinery), unbuildable as UI |
| Psychedelic | SKIP | poster/illustration idiom (liquid type, op-art swirl), illegible at UI scale |
| Future Funk | SKIP | album-art/VHS-collage mood, referenced only for palette/mood inside Retro-Futurism |

## Cluster index — the 11 buildable directions

| # | Direction | Member styles |
|---|---|---|
| 1 | Swiss / Editorial Minimal | Swiss, Modernism, Minimalism, Luxury Minimal, 80's Editorial, Vector Minimalism |
| 2 | Structural / Constructivist Editorial | Bauhaus, Constructivism, Deconstructivism, Post-Modernism, New Wave |
| 3 | Brutalist / Neubrutalist | Brutalism, Neubrutalism |
| 4 | Maximalist | Maximalism, Acid, Experimental Type, Glitch (motion accent) |
| 5 | Memphis / Playful | Memphis, Kidcore, Type Doodles, Naive |
| 6 | Retro-Futurism | Synthwave, Vaporwave (+ Future Funk / Italo Disco for palette/mood only) |
| 7 | Y2K / Chrome | Y2K, Web 2.0 Gloss, Chromecore, Bubbleglam, Cyberpop |
| 8 | Soft Club / Ambient Gradient | Gen X Soft Club |
| 9 | Glass / Spatial | Glassmorphism, Neumorphism, Skeuomorphism |
| 10 | Cyber / Dark-Tech | Cyberpunk, Cyberminimalism, Tech Spec, Surveillance, Blueprint, Glitch (motion) |
| 11 | Luxury Ornamental / Heritage | Art Deco, Mid-Century Modern, 70's Retro |

---

## 1. Swiss / Editorial Minimal

**Traits:** strict 12-col grid, hairline gutters, asymmetric composition, huge
type/whitespace contrast, tabular project indexes not shadowed cards, mono
eyebrow numbering (01/02), restraint as the argument.

**Color:** single-accent mono. Swiss Paper: bg `#F5F3EF`=oklch(96.5% 0.006
84.6), ink `#111111`=oklch(17.8% 0 89.9), accent Swiss red `#DA291C`=oklch(57.5%
0.213 29.6). Alt Cool Blue Mono: bg `#FFFFFF`, ink `#111318`=oklch(18.7% 0.011
268.1), accent `#1B4DFF`=oklch(52.4% 0.265 264.9), muted `#8A8A85`=oklch(63.2%
0.007 106.6). Dark: bg `#0E0E10`=oklch(16.5% 0.004 285.9), text
`#F2F1EC`=oklch(95.8% 0.007 97.4), brighten accent to `#4C6BFF`=oklch(59.2%
0.222 269.4) — never desaturate the accent on dark.

**Type:** Headline Archivo 700–900 tight tracking (or Big Shoulders Display
condensed); body Inter or IBM Plex Sans 400–500; editorial serif accent
Fraunces italic; labels/eyebrows JetBrains Mono or IBM Plex Mono uppercase
tracked. Aggressive H1/body contrast (96–140px display vs 16–18px body), ratio
1.25–1.333, body line-height 1.5–1.6, negative tracking on display only.

**Layout:** thin hairline nav (wordmark left, 3–4 links right, no shadow); hero
full-bleed left-aligned headline with kicker rule, 60/40 asymmetric image, or
type-only; numbered sections in mono caption; tabular project-index rows with
hover-reveal thumbnail, not bento; equal-width grids with hairline dividers, no
rounded corners/shadows.

**Motion:** Lenis smooth scroll; GSAP ScrollTrigger for line-by-line clip-path
text reveals, pinned section transitions, scrubbed counters; View Transitions
API for index-thumbnail→detail morph; CSS `clamp()` fluid type, subgrid
multi-column. Motion is typographic, never decorative.

**Refs:** pentagram.com, readcereal.com, a24films.com.

**Tier:** Tier 1 static → Tier 2 with reveals. Perf excellent. A11y: near-black
on off-white is AAA; watch line-length on wide viewports, don't drop captions
below 12px.

**Components:** shadcn/ui (nav/dialog/table), Origin UI (forms), React Bits
(GSAP text-reveal).

---

## 2. Structural / Constructivist Editorial

**Traits:** diagonal/rotated compositions, primary triad on black/white,
geometric shapes (circles, bars, diagonals) as structural elements not
decoration, grid-breaking with intentional rule-violation, propaganda-poster
typographic hierarchy, asymmetric but rigorously structured.

**Color:** full-palette but restrained, 3–4 flat colors max, no gradients.
Constructivist Primary: red `#E31E24`=oklch(53.8% 0.214 25.2), black
`#0A0A0A`=oklch(9.8% 0 0), white `#F7F7F5`=oklch(97.1% 0.003 90.0), accent
cobalt `#0047AB`=oklch(40.2% 0.166 260.3). Bauhaus alt: red `#D6001C`=oklch(51.5%
0.209 25.8), yellow `#FFD500`=oklch(89.9% 0.181 95.4), blue
`#005293`=oklch(38.4% 0.128 250.1), black `#1A1A1A`=oklch(15.2% 0 0). Dark:
ground `#121212`=oklch(17.2% 0 0), text off-white `#EDEDE8`=oklch(93.4% 0.005
90.2), keep red/yellow at full saturation as the only color notes — no muting.

**Type:** Headline Archivo Black or Space Grotesk 700 uppercase tracked; New
Wave accent via Archivo Expanded or a stacked/rotated headline split across a
diagonal; body IBM Plex Sans; mono captions IBM Plex Mono for grid-coordinate
and rule-number labels. Big display/body jumps (80–120px vs 16px), frequently
set on an angle.

**Layout:** nav bar broken by a diagonal or full-bleed rule line; hero =
oversized rotated headline word overlapping a geometric shape (circle/bar),
diagonal rules crossing the viewport; sections marked by flat color blocks +
numbered mono labels; asymmetric multi-column grid that intentionally breaks
(text spilling past a column, overlapping elements); cards = flat color panels,
hard black borders, no shadow/radius.

**Motion:** GSAP ScrollTrigger for diagonal-wipe reveals and shape rotation
tied to scroll; CSS `transform: rotate/skew` on scroll-linked panels; View
Transitions for a geometric page-to-page wipe; Motion for hover states where
blocks shift/rotate slightly. Keep motion mechanical and precise, not springy.

**Refs:** bureauborsche.com, studio-feixen.ch, walkerart.org.

**Tier:** Tier 1 static (flat blocks + CSS transforms) → Tier 2 with
scroll-tied rotation/diagonal wipes. Perf fine — mostly CSS + SVG shapes. A11y:
red/black/white is AAA if red is dark enough on white; yellow fails on white —
pair yellow only with black, never as body text on light ground.

**Components:** shadcn/ui base, React Bits (text reveal/split), Origin UI
(forms); geometric primitives are hand-built SVG, not registry-dependent.

---

## 3. Brutalist / Neubrutalist

**Traits:** raw/unstyled-HTML energy even with custom fonts, thick black
outlines, deliberately "undesigned" grid, oversized default-looking buttons,
high-contrast flat blocks. Neubrutalism = brutalism + candy-bright color +
thick borders + comic offset shadows — distinct from raw brutalism's
monochrome starkness.

**Color:** Raw Brutalist mono: bg `#FFFFFF`, ink `#000000`, single accent
yellow `#FFEE00`=oklch(92.1% 0.187 100.4), or pure black/white with no color at
all. Neubrutalist candy: bg `#FFFDF5`=oklch(98.9% 0.014 90.1), ink `#000000`,
accent-1 red `#FF3B30`=oklch(60.4% 0.216 25.3), accent-2 yellow
`#FFD60A`=oklch(88.6% 0.178 95.6), accent-3 blue `#0A84FF`=oklch(58.3% 0.191
255.1), accent-4 green `#34C759`=oklch(73.1% 0.187 145.3). Dark: bg
`#121212`=oklch(17.2% 0 0), borders stay pure black or invert to white, candy
accents at full saturation — Neubrutalism rarely desaturates on dark, contrast
should stay maximal.

**Type:** Headline Space Grotesk 700–800 or Archivo Black; alt playful pairing
Public Sans / Archivo; body Inter or Space Grotesk 400–500; mono
labels/badges JetBrains Mono. Type sits inside thick-bordered boxes; scale is
loud but disciplined (2–3 sizes, not collaged like Maximalism).

**Layout:** nav = thick-bordered bar or bordered pill buttons, no
blur/translucency; hero = oversized headline in a bordered box, offset
hard-shadow button (4–8px solid black shadow, no blur); sections = bordered
card grid, uniform corner radius (0 for raw brutalist, 8–16px for
neubrutalist); every interactive element has a visible 2–4px border + flat
offset shadow; forms/inputs stay "raw" — visible borders, no soft UI.

**Motion:** minimal by design for raw brutalism — CSS-only hover (shadow moves
via `translate(4px,4px)` as the border "pops," or shadow vanishes on
`:active` mimicking a physical button press); Neubrutalist can add GSAP/Motion
snap-transitions using linear or `steps()` easing — never smooth curves, that
undercuts the aesthetic. Lenis optional, often skipped intentionally (raw
scroll is on-brand).

**Refs:** brutalistwebsites.com, gumroad.com, craigmod.com.

**Tier:** Tier 1 native fit — borders/shadows are pure CSS, no JS required →
Tier 2 adds snappy interaction motion. Perf: lightest-weight direction in the
library. A11y: pure black/white is AAA by default; candy accents need
per-pair contrast checks — yellow text on white fails, always pair yellow with
black.

**Components:** shadcn/ui (border overrides work cleanly), Kokonut UI (some
neubrutalist-styled buttons), Origin UI (forms with border overrides); mostly
hand-styled Tailwind — least registry-dependent direction alongside Luxury
Ornamental.

---

## 4. Maximalist

**Traits:** collage layering, clashing saturated color, irregular/collaged
type scale, bento grids with mixed sizes+rotation, marquee/ticker strips,
sticker/badge overlays — controlled chaos over a disciplined IA.

**Color:** drenched/clash. Circus Clash: magenta `#FF2E88`=oklch(66.2% 0.244
1.7), acid lime `#C8FF00`=oklch(92.8% 0.230 124.0), cobalt
`#1E3AF0`=oklch(48.1% 0.266 266.4), blaze orange `#FF6B00`=oklch(70.2% 0.200
45.1), ink `#121212`=oklch(18.2% 0 89.9). Tropical Maximal: coral
`#FF5A36`=oklch(68.4% 0.207 33.9), turquoise `#16C79A`=oklch(73.9% 0.145
168.7), violet `#7B2FF7`=oklch(53.9% 0.266 291.9), sunflower
`#FFC93C`=oklch(86.1% 0.159 86.4), hot pink `#FF3E9A`=oklch(67.8% 0.237
356.9), plum ground `#2B0B3F`=oklch(23.5% 0.095 308.9). Dark-native by
default; light variant swaps ground to cream `#FFF7E8`=oklch(97.8% 0.022
83.3).

**Type:** Headline Unbounded 800–900 (or Bungee); accent Instrument Serif
italic; body Space Grotesk or Manrope; numerals/badges Archivo Black.
Irregular scale — mix 3–4 unrelated sizes/weights per screen, rotate/skew
blocks, negative line-height stacks, text/image z-overlap.

**Layout:** floating pill/badge nav (items can scatter/rotate); hero =
overlapping images/shapes/stickers + one oversized headline word breaking
frame + marquee ticker beneath; sections = bento with mixed sizes+rotation,
per-section color-block backgrounds, horizontal-scroll shelves; cards uneven,
thick outlines, offset comic shadows, rotate on hover.

**Motion:** GSAP ScrollTrigger horizontal shelves + scrubbed parallax collage
(layers at different speeds); Motion spring wiggle/rotate on hover, magnetic
cursor buttons; canvas-confetti / GSAP+SVG burst on interaction; CSS
keyframes looping color-shift/marquee. Respect `prefers-reduced-motion`
aggressively — highest-motion cluster.

**Refs:** mschf.com, katemoross.com, jacquemus.com.

**Tier:** Tier 2 → Tier 3 with WebGL particles. Perf: saturated images +
display fonts inflate payload — lazy-load below fold, subset fonts, watch CLS
from absolutely-positioned collage. A11y: audit EVERY color pair (yellow/lime
on white fails AA), reduced-motion fallbacks mandatory.

**Components:** Magic UI (marquee, bento, animated gradient text,
particles/meteors), React Bits (kinetic text, animated bg), shadcn/ui
structural base.

---

## 5. Memphis / Playful

**Traits:** squiggles/confetti shapes scattered as decoration, bold
primary+pastel clash, thick black outlines on organic blobs, hand-drawn/doodle
accents, bouncy asymmetric layout, friendly rounded type, illustration-forward.

**Color:** Memphis full-palette: bubblegum pink `#FF6FB5`=oklch(72.3% 0.194
353.2), turquoise `#2EC4B6`=oklch(74.1% 0.108 179.6), sunshine yellow
`#FFD23F`=oklch(87.2% 0.164 90.3), grape `#7B61FF`=oklch(58.4% 0.239 280.1),
cream bg `#FFF9EC`=oklch(97.8% 0.020 84.9), ink `#1E1E2E`=oklch(22.1% 0.021
280.4). Kidcore alt (brighter/candier): lime `#B4FF39`=oklch(90.5% 0.221
120.8), sky `#5AC8FA`=oklch(78.6% 0.109 227.4), coral `#FF6B6B`=oklch(67.9%
0.190 22.8), bg white `#FFFFFF`. Dark is rare for this direction (skews
light-native); if needed, deep plum bg `#241B36`=oklch(20.3% 0.052 300.2)
keeps candy accents at full chroma, never muted.

**Type:** Headline Bricolage Grotesque or Unbounded 700–800 (rounded-geometric
warmth); body Manrope 400–500; doodle/accent labels via Instrument Serif
italic for a whimsical contrast note. Rounded, bouncy scale mirrored in
generous corner radii — avoid condensed/sharp faces entirely.

**Layout:** nav = pill-shaped floating bar with a doodle icon accent; hero =
headline with hand-drawn underline/circle SVG scribbles, scattered confetti
shapes (triangles, squiggles, dots) as absolutely-positioned SVG; sections =
rounded bento cards (24px+ radius) with thick 3–4px outlines and a single soft
blurred drop shadow (not offset-hard like Neubrutalism); blob shapes as
section dividers instead of straight lines.

**Motion:** Motion (framer-motion) spring-based wiggle/bounce on hover and
mount (high stiffness, low damping for a "boingy" feel); GSAP ScrollTrigger
for confetti pieces drifting/rotating independently on scroll; CSS keyframe
idle-float on decorative blobs; canvas-confetti burst on CTA click. Motion
should read toy-like, never smooth-corporate.

**Refs:** mailchimp.com, duolingo.com, headspace.com.

**Tier:** Tier 1 static with CSS-only wiggle/hover states → Tier 2 for spring
physics and confetti bursts; genuinely benefits from Tier 2 to sell the "alive"
feel, reads flat without motion at Tier 1. Perf: SVG illustrations are cheap;
watch total independently-animated shape count on hero. A11y: pastel-on-pastel
text fails contrast easily — always set body text in ink, never brand pastel;
provide a reduced-motion static state for bounce/spring.

**Components:** React Bits (playful hover/text effects), Magic UI (confetti,
animated blobs), Motion Primitives (spring hover primitives), shadcn/ui
structural base.

---

## 6. Retro-Futurism

**Traits:** horizon-grid perspective, chrome/neon gradient type, sun/circle
motif, scanlines, VHS-glitch texture, 80s-futurism nostalgia, high-contrast
neon-on-dark.

**Color:** Synthwave dark-native: void bg `#0D0221`=oklch(13.4% 0.052 300.1),
hot magenta `#FF2CDF`=oklch(65.8% 0.286 335.4), electric cyan
`#00F5FF`=oklch(89.3% 0.146 200.2), deep violet `#8B2FC9`=oklch(45.2% 0.229
300.4), sunset orange `#FF7A00`=oklch(70.4% 0.187 50.2) for the horizon-sun
gradient. Vaporwave alt (pastel/lighter mood): pink `#FF71CE`=oklch(74.8% 0.191
350.1), lavender `#B967FF`=oklch(64.7% 0.221 300.3), mint `#01CDFE`=oklch(73.9%
0.138 209.8), pale bg `#FFF3F9`=oklch(96.4% 0.019 350.6) — vaporwave is the rare
light-leaning member of this cluster, though still commonly rendered dark.
Strategy: dark-native duotone neon glow on near-black; never desaturate on a
forced "light mode" — swap only the ground, keep neons saturated.

**Type:** Headline Unbounded 800 or Big Shoulders Display (condensed,
poster-like) with a neon-glow text-shadow; body Space Grotesk or JetBrains
Mono (mono reinforces the retro-computer feel) 400–500; terminal accents in
JetBrains Mono uppercase tracked. Consider gradient-fill hero text
(`background-clip: text`, magenta→cyan) for the headline word.

**Layout:** nav = thin bar over the void, wordmark with neon-glow hover; hero =
perspective horizon-grid (CSS 3D transform floor grid or SVG), oversized
sun/circle with horizontal gradient bands behind the headline, scanline
overlay texture; sections = dark cards with a 1px neon-gradient border, glow
on hover; dividers = neon horizontal rule with glow blur.

**Motion:** CSS-only scanline/glow via animated `background-position` and
pulsing `box-shadow` (cheap, on-brand); GSAP ScrollTrigger to animate
horizon-grid perspective/parallax and sun position on scroll; Motion for
neon-glow hover intensification on cards/buttons; occasional VHS-glitch
micro-interaction (`clip-path` jitter) on hover only, never ambient — hurts
readability and perf. `filter: drop-shadow` beats heavy blurred `box-shadow`
for glow perf.

**Refs:** hotlinemiami.com, and Awwwards' Synthwave-tagged portfolio/campaign
collection. Flag: this is a niche/indie aesthetic — no major evergreen brand
runs pure synthwave long-term the way Linear runs glass; treat named refs as
directional and verify current URLs at spec time (time-limited campaign/
portfolio pieces, not permanent flagships).

**Tier:** Tier 1 CSS-only gradient+grid (static horizon, CSS glow) → Tier 3 for
a true animated 3D grid-floor (R3F plane with a scrolling grid shader) and
animated sun. Perf: glow effects are cheap in moderation but stack fast —
budget glow layers; scanline overlays as one `repeating-linear-gradient`, not
per-element. A11y: neon-on-black is high contrast but saturated magenta/cyan at
body-copy size can cause visual vibration/eye strain — reserve neon for display
type and CTAs, keep body copy off-white at 70–85% opacity.

**Components:** React Bits (glow/gradient text, grid backgrounds), Aceternity
UI (background beams, spotlight, meteor effects), Magic UI (animated gradient
text, retro-grid background component).

---

## 7. Y2K / Chrome

**Traits:** chrome/liquid-metal gradients, glossy bubble buttons (Web 2.0
"aqua" gloss), bevel + specular highlight on shapes, translucent plastic
(iMac-era), star/sparkle accents, rounded-everything, early-internet nostalgia
rendered with modern polish.

**Color:** Chrome/Metallic base — gradient IS the palette, not a flat swatch:
silver stops `#E8E8ED`→`#B8B8C4`→`#FFFFFF` (roughly oklch 92%/74%/100% at
~0.006 chroma, hue 285), accent hot pink `#FF10F0`=oklch(65.9% 0.311 340.2),
electric blue `#00C2FF`=oklch(78.4% 0.138 220.1), lime accent
`#CCFF00`=oklch(93.2% 0.221 118.4), bg white/pearl `#F7F7FA`=oklch(97.5% 0.006
285.3). Bubbleglam alt (candy-plastic): bubblegum `#FF8FD6`=oklch(78.1% 0.147
345.2), grape soda `#C9A3FF`=oklch(78.3% 0.113 300.4), mint
`#B4F8C8`=oklch(90.4% 0.109 155.1), bg cream `#FFFCF5`=oklch(98.5% 0.012 90.1).
Dark is less native to this direction (Y2K skews light/pearlescent); if
needed, swap bg to graphite `#1C1C24`=oklch(20.8% 0.011 285.2), let chrome
gradients + neon accents carry contrast, gloss highlights go brighter/whiter.

**Type:** Headline Unbounded 700–800 (rounded-geometric weights read Y2K); alt
sharper chrome feel via Space Grotesk 700; body Manrope or Inter 400–500;
sparkle/badge labels in Archivo Black small-caps. Consider a metallic-gradient
text-clip for the hero headline (silver→white→silver linear-gradient with
subtle noise).

**Layout:** nav = glossy pill bar with a bevel highlight (inset white gradient
on the top edge); bubble buttons with a radial-gradient specular highlight
(Aqua/iTunes-era gloss); hero = chrome 3D shape (sphere/blob) or
gradient-clip headline + scattered star/sparkle SVG accents; sections =
glossy rounded cards (20px+ radius) with a soft top highlight and bottom
shadow, faux-3D bevel via layered `box-shadow` (inset light + outer dark);
dividers = chrome bar or gradient rule.

**Motion:** CSS-only gloss via layered `radial-gradient` + `box-shadow: inset`
(cheap, achieves the plastic-highlight look without JS); Motion for bouncy
spring hover on bubble buttons (scale+glow); GSAP for a slow chrome-gradient
shimmer sweep across text/shapes (`background-position` animation on a
gradient-clip headline); sparkle/star particles via a registry particle
component or CSS-animated SVG twinkle. Keep motion glossy-smooth, not
glitchy — that's the Cyber cluster's job.

**Refs:** early-2000s revival brand drops on Awwwards tagged Y2K, current
Y2K-revival fashion/beauty DTC micro-sites. This is a fast-moving revival trend
more visible in fashion-brand drops and Dribbble/Pinterest concept work than a
small set of permanent flagship URLs — treat named refs as directional, verify
the current live example before quoting to a client.

**Tier:** Tier 2 native fit (gloss/bevel reads best with real gradient
rendering + hover motion) → degrades to Tier 1 by flattening gloss to a single
soft gradient card + static highlight (loses the "wet plastic" feel, stays
clean); Tier 3 rarely justified unless a literal 3D chrome hero object is the
ask (then R3F + a metallic/reflective material). Perf: gradient-heavy but
CSS-only, cheap; cap stacked `box-shadow` layers per card to 3. A11y:
chrome/pearl-on-white can be LOW contrast for body text — always sit body copy
on a solid ink color, never directly on a gloss gradient; neon accents (lime,
hot pink) fail AA as text on white — accent-only, never body copy.

**Components:** Aceternity UI (3D card hover, glowing borders suit chrome
bevels), Magic UI (shimmer button, sparkles/particles, gradient text), React
Bits (metallic/gradient text effects), shadcn/ui base.

---

## 8. Soft Club / Ambient Gradient

**Traits:** airbrushed ambient gradient-mesh backgrounds, soft-focus glow
orbs, low-contrast pastel-on-pastel with one saturated grounding accent,
generous whitespace, wellness/lifestyle-brand calm, blurred color-field
sections instead of hard blocks. Sole member Gen X Soft Club is ADAPT-tagged
in isolation — this direction earns its BUILD status through the layout
discipline around it, not the palette alone.

**Color:** dusty lavender `#C9B8E8`=oklch(84.1% 0.061 300.2), blush
`#F3C9D9`=oklch(87.3% 0.052 350.4), sage `#C4D9C4`=oklch(86.2% 0.041 145.3),
warm sand bg `#F7F1E8`=oklch(95.5% 0.020 75.2), single saturated grounding
accent terracotta `#D97757`=oklch(65.8% 0.132 40.1) or deep plum
`#5B3A6E`=oklch(38.4% 0.112 305.2) for text/CTA. Strategy: single-accent on a
low-chroma gradient field — the mesh blends 3–4 pastel hues, ONE higher-chroma
accent is reserved for CTAs/links only. Dark: dusk bg `#1A1620`=oklch(16.8%
0.032 305.1), same pastel family pushed into low-opacity glow-orb blooms rather
than flat fills, accent brightens to coral `#F0937A`=oklch(76.2% 0.128 40.3)
for visibility.

**Type:** Headline Fraunces or Instrument Serif (soft serif warmth, airy
editorial-wellness feel); body Manrope or Inter 400, light–medium weights only
— heavy/black weights fight the softness; labels in a light-tracked sans,
never mono (too technical for this cluster). Calm scale: H1 48–72px, body
16–18px, line-height 1.6+.

**Layout:** nav = minimal, transparent-over-gradient, floats without a hard
bar; hero = full-viewport ambient gradient mesh (blurred color blobs) behind a
centered or left-aligned soft-weight headline, no hard shapes; sections =
generous whitespace, content floats on the gradient field rather than sitting
in cards; where cards appear they're very soft — 24–32px radius, near-white
translucent fill, minimal border, diffused shadow only.

**Motion:** CSS `@property` + conic/radial-gradient animation for a
slow-drifting mesh background (the signature move — blobs migrate over
20–40s loops, no JS); Lenis smooth scroll reinforces the floaty feel; Motion
for gentle fade+drift on scroll-into-view (large y-offset, long duration,
`easeOut` — never springy, that's Memphis's job); GSAP ScrollTrigger only for
slow parallax between gradient layers. Lowest motion-intensity direction after
Swiss — restraint IS the aesthetic.

**Refs:** headspace.com, calm.com. Beyond these two durable anchors, most
examples live in DTC wellness/beauty marketing pages tagged "soft gradient" on
Awwwards/Land-book — trend-vocabulary more than a fixed brand list.

**Tier:** Tier 1 static (one pre-rendered gradient-mesh image or a static CSS
gradient, no animation) → Tier 2 for the living drifting-mesh background,
where this direction actually sings; Tier 3 unnecessary (a shader-based fluid
gradient is possible but rarely worth the WebGL cost over a good CSS
conic-gradient loop). Perf: CSS gradient animation is near-free; if using a
blurred-image mesh, ship one optimized background asset, not multiple
`backdrop-filter`-blurred DOM layers (stacking gets expensive fast). A11y:
highest-risk direction for text contrast — pastel-on-pastel body text
routinely fails AA; mandate the single saturated accent or near-black ink for
ALL body copy, pastels stay decoration-only, never text.

**Components:** Magic UI (animated gradient background, meteors/orbs), Motion
Primitives (fade/drift-in scroll primitives), shadcn/ui base — needs the
fewest "flashy" registry components of any direction, mostly a good gradient
treatment plus restrained motion.

---

## 9. Glass / Spatial

**Traits:** frosted translucent panels floating over color/gradient/3D, soft
ambient shadows, thin 1px highlight borders, rounded-xl corners, restrained
mid-weight type, real z-depth via parallax.

**Color:** duotone accent on neutral, light + dark. Glass Daylight (light):
ground `#F0F4F8`=oklch(96.5% 0.007 247.9), signal blue `#2F6FED`=oklch(57.4%
0.202 262.0), lilac `#7C5CFC`=oklch(59.7% 0.226 286.5). Glass Midnight
(dark-native): void `#0B0E14`=oklch(16.3% 0.014 264.1), teal glow
`#5EEAD4`=oklch(85.5% 0.125 181.1), violet glow `#8B5CF6`=oklch(60.6% 0.219
292.7). Glass surfaces: light `rgba(255,255,255,0.55–0.7)` fill +
`rgba(255,255,255,0.4)` 1px border; dark `rgba(255,255,255,0.05–0.08)` fill +
`rgba(255,255,255,0.12)` 1px border. Accent colors live in the glow/gradient
BEHIND the glass, not on it.

**Type:** Geist (headline+body, variable 400–700) reads clean over blur; Geist
Mono or JetBrains Mono for data labels. Alt: Sora headline + Manrope body +
IBM Plex Mono labels. Keep weight 400–600 — no ultra-black, it competes with
the blur. Small-caps/mono labels for readouts.

**Layout:** floating pill nav detached from the top edge, backdrop-blur +
translucent fill + 1px border, hovers above content; hero = layered glass
cards over an animated gradient-mesh or soft 3D, depth via
blurring/parallaxing layers at different scroll speeds; sections = bento of
glass cards (dashboard register), frosted panel + soft inner shadow + floating
icon; cards 16–24px radius, 16–24px backdrop-blur, ambient shadow, hover lift
+ slight blur/brightness increase.

**Motion:** CSS `backdrop-filter` + layered `box-shadow` is the base material
(no JS); GSAP parallax depth between glass layers; Motion spring tilt/lift on
hover, draggable cards; Lenis smooth scroll sells depth; animated
mesh-gradient via CSS `@property` + conic-gradient, or a light shader plane
(react-three-fiber) for a true animated blob behind glass; View Transitions
for card→detail expand.

**Refs:** apple.com (Vision Pro pages), linear.app, raycast.com.

**Tier:** Tier 2 → Tier 3 with WebGL. Perf: `backdrop-filter` blur is
GPU-heavy — cap simultaneous blurred layers, avoid `will-change` overuse, ship
a solid-fill fallback for `prefers-reduced-transparency`. A11y: enforce a
scrim/contrast layer behind translucent text (never rely on blur alone for
legibility); respect `prefers-contrast` and `prefers-reduced-transparency`.

**Components:** Aceternity UI (glow/spotlight cards, background beams, 3D card
hover), Cult UI + Kokonut UI (glass/3D card, dock), Motion Primitives
(tilt/hover), shadcn/ui base.

---

## 10. Cyber / Dark-Tech

**Traits:** dark-native UI, terminal/HUD readouts, thin hairline grids,
monospace data labels, scanline/glitch texture as accent (not ambient),
crosshair/reticle micro-marks, blueprint schematic linework, neon-on-black —
colder and more restrained than synthwave, signal color not party color.

**Color:** Cyberpunk dark-native: void bg `#08090C`=oklch(10.6% 0.006 260.1),
signal cyan `#00FFC2`=oklch(87.8% 0.171 165.2) or acid green
`#39FF14`=oklch(87.1% 0.271 135.4), warning red `#FF003C`=oklch(58.2% 0.241
15.1), muted grid-line gray `#2A2E35`=oklch(27.3% 0.012 250.2). Blueprint alt
(schematic, cooler/quieter): deep blueprint blue bg `#0A2540`=oklch(27.4% 0.083
250.3), linework `#7FDBFF`=oklch(82.1% 0.091 220.2), paper-white annotations
`#E8EEF4`=oklch(92.9% 0.010 240.1). Tech Spec / Cyberminimalism alt (closer to
Swiss but dark): near-black `#101114`=oklch(14.1% 0 0), single signal accent
(electric blue `#2F6FED` or lime `#A6FF00`=oklch(91.4% 0.230 118.2)), everything
else grayscale. Dark is native across the whole cluster; a light variant
(mainly Tech Spec/Blueprint print-style docs) swaps to paper
`#F4F1EA`=oklch(94.8% 0.012 85.2) with ink-blue linework, neon reserved for
interactive elements only.

**Type:** Headline JetBrains Mono or IBM Plex Mono at display size — unusual
but on-brand, mono-as-display is this cluster's signature move — or Space
Grotesk 600–700 for a more "product" cyberpunk feel; body IBM Plex Sans or
Inter; data/telemetry labels always mono, uppercase tracked, often bracketed
(`[ STATUS ]`) or with a blinking-cursor treatment. Tight, technical scale —
less display/body contrast than Swiss, more uniform "console" sizing.

**Layout:** nav = thin-line bar with bracket-style `[MENU]` labels,
corner-tick crosshair marks at viewport edges (pure CSS `::before/::after`);
hero = headline over a faint animated grid/scanline background, HUD-style
corner readouts (coordinates, status text) framing the composition; sections =
bordered panels with 1px hairline borders (not shadow), terminal-style section
headers (`// 01 — ABOUT`); cards = dark panels, thin glowing border on hover,
occasional glitch-clip micro-effect on hover only.

**Motion:** GSAP ScrollTrigger for scanline sweep and typewriter/decrypt text
reveal (characters cycle through random glyphs before settling — classic
"hacker terminal" effect); CSS `clip-path` animation for glitch-jitter accents,
triggered on hover or section-enter only, never looping ambiently (fatiguing,
hurts perf); Lenis optional; View Transitions for a "system boot" style page
transition; blinking cursor via CSS `steps()` animation. Motion should feel
precise/mechanical — `steps()`/linear easing common — rather than organic.

**Refs:** linear.app (cyberminimalism-adjacent — dark, precise, signal-color
restraint), rive.app (dev-tool dark UI with technical polish); hardware/
robotics product sites for the Blueprint/schematic sub-mode (verify current
example at spec time — this sub-mode moves with whichever hardware brand is
shipping a site refresh).

**Tier:** Tier 1 static for the Blueprint/Tech Spec sub-modes (hairline grid +
mono labels is CSS-only) → Tier 2 for scanline/glitch/decrypt-text motion,
where Cyberpunk proper needs to live to read as more than "dark theme with
mono font"; Tier 3 for an animated 3D HUD/particle-field hero. Perf:
glitch/scanline effects are cheap in CSS but easy to overdo — cap to
hover/enter triggers; decrypt-text on long copy blocks hurts perceived load
speed, reserve for headlines only. A11y: acid green/signal cyan on near-black
is high contrast, usually AA/AAA at large sizes but verify at body-copy
weight; respect `prefers-reduced-motion` aggressively for glitch/flicker —
never strobe above ~3Hz, photosensitivity risk.

**Components:** Aceternity UI (background beams, spotlight, glowing/animated
borders), React Bits (glitch text, decrypt/scramble text effects, grid
backgrounds), Magic UI (Terminal / typing-code block component), shadcn/ui
base.

---

## 11. Luxury Ornamental / Heritage

**Traits:** symmetrical ornamental geometry (sunburst, fan, chevron, ziggurat
motifs), gold/brass line accents on deep color grounds, warm heritage
palettes, generous formal whitespace, serif-forward type with old-world
elegance. Mid-Century sub-mode = organic curves + warm wood-tone palette +
atomic/boomerang shapes; 70s sub-mode = earthy warm palette + rounded-geometric
type + groovy curved dividers.

**Color:** Art Deco: deep emerald `#0B3D2E`=oklch(30.2% 0.062 155.3), gold/brass
`#C6A15B`=oklch(72.4% 0.092 75.2), black `#0A0A0A`=oklch(9.8% 0 0), ivory
`#F5F0E1`=oklch(95.1% 0.022 85.1). Alt Deco Noir: midnight navy
`#0D1B2A`=oklch(19.8% 0.032 250.2), gold `#D4AF37`=oklch(75.6% 0.112 85.3),
cream `#FAF6EE`=oklch(97.2% 0.015 85.1). Mid-Century Modern: burnt orange
`#C1502E`=oklch(55.8% 0.148 35.2), avocado `#6B8E4E`=oklch(56.2% 0.104 130.1),
mustard `#E3A857`=oklch(76.4% 0.113 75.4), walnut brown bg
`#3E2A1F`=oklch(26.8% 0.041 45.2), cream `#F2E9DA`=oklch(94.2% 0.024 80.1).
70's Retro: rust `#B5502F`=oklch(52.6% 0.139 35.1), harvest gold
`#D9A441`=oklch(75.3% 0.121 80.2), chocolate brown `#4A2E2A`=oklch(24.6% 0.028
30.1), orange-cream bg `#F7E7CE`=oklch(92.4% 0.048 75.3). Strategy varies by
sub-style: Deco is dark-ground-with-metallic-line, MCM/70s are
light-cream-with-earth-tones — two genuinely different default modes. Dark
mode for MCM/70s (less native) just deepens toward the walnut/chocolate values
already listed; Deco's dark-native mode deepens emerald/navy further and keeps
gold luminous — never desaturate metallic gold, it should look like it's
catching light.

**Type:** Deco headline — Fraunces (elegant high-contrast serif weights) at
display size with wide tracking on small-caps labels, or a geometric-deco feel
via Big Shoulders Display condensed caps; body Inter or IBM Plex Sans. MCM
headline — Space Grotesk or Bricolage Grotesque 600–700 (rounded-geometric
reads mid-century); body Manrope. 70s headline — Bricolage Grotesque or
Unbounded (warm rounded-geometric); accent Instrument Serif italic for a
groovy editorial note. Across the cluster: generous letter-spacing on
caps/labels signals "formal heritage" the way tight tracking signals
Swiss-modern.

**Layout:** nav = centered symmetrical wordmark, thin gold/brass rule beneath
(Deco) or a warm solid-color bar with rounded pill links (MCM/70s); hero —
Deco: symmetrical sunburst/fan SVG motif radiating behind a centered headline,
thin gold line borders framing the viewport; MCM: asymmetric split with an
organic boomerang/kidney-bean shape as an image mask; 70s: curved/scalloped
SVG-wave section divider instead of a straight line. Sections = framed content
blocks with a thin ornamental border (Deco), or rounded-corner warm-toned
cards with a slightly grained/textured background (MCM/70s, evokes vintage
paper); dividers are geometric ornament (chevron row, sunburst fragment,
scallop), not plain hairlines.

**Motion:** CSS-only ornamental line-draw (SVG `stroke-dashoffset` animation
for sunburst/chevron reveal on scroll-into-view — elegant, cheap); GSAP
ScrollTrigger for symmetrical reveal (mirrored elements animate in from both
sides simultaneously, reinforcing the symmetry); View Transitions for a
formal cross-fade between pages — no bounce/spring, this cluster wants
composed, unhurried motion; grain/texture overlay via a static SVG noise
filter, not animated. Pace is slow and deliberate — the opposite tempo from
Memphis or Y2K.

**Refs:** Deco: luxury-hospitality and champagne-house brand microsites (verify
current live example, this category turns over with campaign cycles). MCM:
hermanmiller.com — a durable, currently-live anchor for MCM-adjacent brand
design. 70s: contemporary "retro revival" hospitality/record-label sites —
harder to name one durable evergreen flagship, flag as trend-vocabulary and
verify at spec time.

**Tier:** Tier 1 static fits the cluster well (ornamental SVG line-art is
cheap, symmetry doesn't require motion to read) → Tier 2 for scroll-triggered
line-draw reveals and mirrored-symmetry animation, the natural ceiling for
most of this cluster; Tier 3 rarely justified (no strong 3D/immersive case
unless the brand is literally hospitality/real-estate needing a walkthrough).
Perf: SVG ornament is lightweight; use CSS/SVG noise for grain, not a raster
texture file. A11y: gold-on-dark-emerald/navy (Deco) needs a contrast check —
brass/gold at typical luminance can dip below AA for body text on deep green,
verify or lighten gold for text use vs. decorative-only use; earth-tone-on-
cream (MCM/70s) is generally safe but check mustard/harvest-gold text
specifically.

**Components:** shadcn/ui base — this cluster leans hand-crafted SVG ornament
over registry components, least registry-dependent alongside Brutalist. React
Bits (line-draw/SVG reveal primitives), Origin UI (elegant form styling).
