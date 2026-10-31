# Page Composition — reference

Section-archetype menu + page-narrative rules. Spacing scale and general
layout mechanics live in impeccable `layout.md` — this file governs which
sections exist, how often, and in what order.

## How to use

1. This file supplies the section-archetype menu and the binding rules that
   stop a page reading as repeated identical units.
2. Spacing system, visual rhythm mechanics, and card-monotony principle stay
   in impeccable `layout.md` — deferred, not restated, except where this file
   adds a binding numeric cap on top.

## Section-archetype menu per direction

4–6 named archetypes per direction, always including a closing CTA. Fixes two
named defects: "4 identical H2+para+CTA units, same cadence" and
"every section is centered-heading + grid".

| Direction | Archetypes |
|---|---|
| Swiss / Editorial Minimal | type-only hero · tabular index · numbered-process band · editorial pull-quote · asymmetric split · closing CTA |
| Structural / Constructivist Editorial | diagonal-wipe hero · color-block manifesto · rotated-shape gallery · numbered-label grid · propaganda pull-quote · closing CTA |
| Brutalist / Neubrutalist | raw stacked-text hero · bordered-card grid · oversized-button CTA band · offset-shadow testimonial stack · terminal-style spec list · closing CTA |
| Maximalist | collage hero · bento shelf · marquee strip · sticker-badge gallery · horizontal-scroll shelf · closing CTA |
| Memphis / Playful | doodle hero · rounded-bento cards · blob-divider feature band · illustrated process steps · confetti testimonial wall · closing CTA |
| Retro-Futurism | horizon-grid hero · neon-bordered feature cards · scanline stat band · chrome pull-quote · terminal-glow gallery · closing CTA |
| Y2K / Chrome | gloss hero · bubble-button feature row · sparkle testimonial carousel · chrome stat band · bevel-card gallery · closing CTA |
| Soft Club / Ambient Gradient | gradient-mesh hero · floating-text feature band · soft-card testimonial cluster · breathing-space pull-quote · gentle process steps · closing CTA |
| Glass / Spatial | layered-glass hero · bento dashboard · frosted feature cards · depth-parallax gallery · glass pull-quote panel · closing CTA |
| Cyber / Dark-Tech | HUD hero · bracketed spec panel · terminal-log feature list · decrypt-text testimonial · hairline-grid gallery · closing CTA |
| Luxury Ornamental / Heritage | symmetrical sunburst hero · framed ornamental feature grid · formal pull-quote · scalloped-divider process band · heritage gallery · closing CTA |

## Adjacency + repetition caps (binding)

- No two adjacent sections share an archetype.
- No archetype appears more than 2× on one page. Prior defect: "cards FIRED ×4" —
  the exact defect this cap exists to block.
- Impeccable `layout.md`'s card-monotony principle is a deferred pointer; the
  numeric caps above are this file's own addition, not restated from there.

## Mandatory closing CTA

Every page ends with a dedicated CTA section — not a footer link, a real
section. Prior defect: "no closing-CTA section" was a fired defect.

## One oversized signature element per page

Exactly one section breaks scale or grid dramatically per page — e.g.
A business's hours table used as an oversized design feature. Impeccable
`brand.md` grants the permission for this; this file makes it a mandate, not
an option.

## Section transitions / narrative pacing

- Density alternation between sections — pointer to impeccable `layout.md`
  §Create Visual Rhythm, don't restate.
- Connective elements (dividers, transitions) drawn from the direction's own
  motion vocabulary — pointer to `motion-library.md`.
- One dominant idea per fold — a section trying to make two points reads as
  neither.

## De-registry-fication procedure

Pulled registry components carry three signature tells: default radius,
default shadow/glow, default easing/duration. Override ALL THREE against the
direction's tokens — overriding color alone leaves the registry's fingerprint
intact.

| Direction | Tell to break first |
|---|---|
| Swiss / Editorial Minimal | radius — registry rounded corners become hairline square edges; no shadow to begin with; easing goes linear/precise, never springy |
| Structural / Constructivist Editorial | easing — registry ease-out becomes mechanical linear/`steps()`; radius to 0; shadow removed for flat color blocks |
| Brutalist / Neubrutalist | radius — any rounded corner is the #1 tell, force 0 or a thick-border override; shadow goes hard-offset, no blur; easing linear/`steps()`, never a smooth curve |
| Maximalist | shadow/glow — registry soft shadow becomes offset comic-shadow or none; radius made uneven per card on purpose; easing goes spring/wiggle |
| Memphis / Playful | easing — registry ease-out becomes high-stiffness/low-damping spring; radius oversized (24px+); shadow soft-blurred, never offset-hard |
| Retro-Futurism | shadow/glow — registry soft shadow becomes neon `drop-shadow` glow, not a blurred box-shadow; radius sharp/angular outside the chrome sub-mode; easing linear for scanline/glitch |
| Y2K / Chrome | shadow/glow — registry flat shadow becomes layered inset+outer bevel gloss; radius 20px+ pill/rounded; easing bouncy spring on hover |
| Soft Club / Ambient Gradient | shadow/glow — registry hard shadow becomes diffused/ambient or removed; radius 24–32px soft; easing slow `easeOut`, never spring |
| Glass / Spatial | blur+glow — the registry's default glass preset gets re-tuned to the direction's own accent, never shipped at library defaults; radius 16–24px; easing moderate spring tilt/lift |
| Cyber / Dark-Tech | easing — registry ease becomes `steps()`/linear, mechanical; radius to 0, hairline borders instead of shadow; glow reserved for hover only |
| Luxury Ornamental / Heritage | easing — registry ease-out slows to deliberate, no bounce; radius 0 (Deco framed) or soft (MCM/70s rounded-warm) per sub-style; shadow removed for ornamental line-borders |

## Content-density corollary

A section with no real research fact backing it is a removal candidate, not a
padding target — see `copy-voice.md` §Specificity-from-research rule.
