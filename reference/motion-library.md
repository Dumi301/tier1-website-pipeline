# Motion Library — reference

The workflow's motion vocabulary. One recipe per technique — read GOLDEN RULES
and TOOL SELECTION first, then jump to the technique you need.

## Golden rules

1. **Animate transform/opacity first.** These are compositor-only properties —
   everything else (`width`, `top`, `left`, `background-color` at scale) risks
   layout/paint and drops frames. Reach for `translate`/`scale`/`rotate`/`opacity`
   before anything else.
2. **Ease-out for entrances.** Things entering the screen should decelerate into
   place (fast start, slow settle) — it reads as arriving under momentum, which
   feels natural. Ease-in is for exits.
3. **Duration: 200–300ms for UI**, longer (400ms+) for scroll-driven or large-
   surface moves. Sub-100ms reads as a glitch; over 400ms on a button press reads
   as sluggish.
4. **Exits ~75% of the enter duration.** Something leaving the screen should feel
   quicker than it arrived — asymmetric timing keeps the UI feeling responsive.
5. **ALWAYS a `prefers-reduced-motion` fallback.** Non-negotiable on every
   technique below — either skip the animation entirely (jump to end state) or
   reduce it to a simple opacity crossfade.
6. **Motion must guide, give feedback, or build continuity — never decorate.**
   Every animation should answer "what is this telling the user" (where did this
   come from, did my action register, how do these two states relate). If the
   answer is "it looks cool," cut it or move it to a Tier 3 storyboarded moment
   where that's explicitly the point.

## Interaction-states contract (binding)

1. **Every interactive control ships hover + active + focus-visible.** Active
   is the pointer-down acknowledgment — the state between hover and the
   action completing. A prior review found "not one control responded to
   pointer-down, `active:` count = 0" across ~60 controls. Missing any of the
   three is a defect, not a style choice.
2. **Same semantic role = same behavior, site-wide.** One CTA that lifts in
   one place, darkens in another, and grows in a third is a defect even
   though each individual state looks fine in isolation — the inconsistency
   itself is the tell.
3. **Reduced-motion must disable JS/GSAP tweens too, not just CSS.** A
   `prefers-reduced-motion` media query that only guards CSS transitions
   while GSAP tweens keep running is an incomplete guard. Use a kill-switch
   pattern — `gsap.matchMedia()` or a global reduced-motion flag checked
   before any tween fires — so JS-driven motion actually stops.

## Tool selection

- **GSAP + ScrollTrigger** — now 100% FREE including SplitText, ScrollSmoother,
  and MorphSVG since v3.13 (Webflow acquired GreenSock Oct 2024, dropped the Club
  GreenSock paywall). Reach for it for scroll-driven, timeline, pin, and scrub
  work — nothing else in the stack matches its scroll-linked timeline control.
- **Motion** (was Framer Motion; import from `"motion/react"`) — declarative React
  enter/exit, layout animation, and gestures. Leaner than GSAP for component-level
  UI (hover, tap, `AnimatePresence`, shared layout transitions).
- **Lenis** (package `lenis`, formerly `@studio-freight/lenis`, now maintained
  under darkroom.engineering) — smooth/inertia scroll. Pairs with GSAP
  ScrollTrigger or R3F for scroll-synced scenes; don't reach for it standalone
  without a reason to smooth native scroll.
- **Three.js / React Three Fiber + drei** — full 3D/WebGL, shader backgrounds.
  Tier 3 only.
- **View Transitions API** — native page/route morphs, zero JS animation library
  needed. Built into Astro (`<ClientRouter />`). Best fit for MPA sites given the
  Firefox cross-document View Transitions gap (same-document transitions work
  everywhere; cross-document is Chromium-only as of this writing — Astro's MPA
  transitions degrade gracefully where unsupported).
- **GSAP SplitText / Splitting.js / SplitType** — kinetic text splitting into
  chars/words/lines for staggered reveals. SplitText is now free with GSAP;
  Splitting.js/SplitType are lightweight zero-dep alternatives when you don't
  need the rest of GSAP.

**Consensus split:** Motion for UI enter/exit + layout animation, GSAP for
scroll/timeline work. Don't reach for GSAP to animate a dropdown, and don't
reach for Motion to pin a section.

## Recipes

### Scroll-triggered reveal
- **Good for:** elements fading/sliding in as they enter the viewport — the most
  common Tier 2 motion move.
- **Tool:** GSAP ScrollTrigger (`toggleActions`) or Motion `whileInView`.
- **Sketch (GSAP):**
  ```js
  gsap.from(".reveal", {
    opacity: 0, y: 24, duration: 0.5, ease: "power2.out",
    scrollTrigger: { trigger: ".reveal", start: "top 85%", toggleActions: "play none none reverse" }
  });
  ```
- **Sketch (Motion):**
  ```jsx
  <motion.div
    initial={{ opacity: 0, y: 24 }}
    whileInView={{ opacity: 1, y: 0 }}
    viewport={{ once: true, margin: "-15%" }}
    transition={{ duration: 0.5, ease: "easeOut" }}
  />
  ```
- **Tier fit:** T2, T3.
- **Reduced-motion fallback:** skip the transform, keep only an opacity crossfade
  (or render the end state immediately).
- **Perf note:** batch reveals with one ScrollTrigger per group where possible
  (`gsap.utils.toArray` + a shared trigger) rather than one instance per element.

### Parallax
- **Good for:** background/foreground layers moving at different rates for depth
  — hero sections, section dividers.
- **Tool:** GSAP ScrollTrigger `scrub: true`, or pure-CSS `animation-timeline:
  scroll()` where browser support allows.
- **Sketch (GSAP):**
  ```js
  gsap.to(".layer-bg", { yPercent: 20, ease: "none",
    scrollTrigger: { trigger: ".hero", start: "top top", end: "bottom top", scrub: true } });
  ```
- **Sketch (CSS, Tier 1 only):**
  ```css
  .layer-bg { animation: parallax linear; animation-timeline: scroll(); }
  @keyframes parallax { to { transform: translateY(20%); } }
  ```
- **Tier fit:** T1 (CSS version), T2, T3 (GSAP).
- **Reduced-motion fallback:** disable the scrub entirely, render layers static.
- **Perf note:** `scrub` ties directly to scroll position, so it's cheap (no RAF
  loop of its own) — but keep layer count low on mobile; each extra scrubbed
  layer adds a ScrollTrigger recalculation on resize.

### Sticky / pinned section
- **Good for:** a section that holds in place while content scrolls past/through
  it — feature walkthroughs, storytelling scenes.
- **Tool:** GSAP ScrollTrigger `pin: true`.
- **Sketch:**
  ```js
  ScrollTrigger.create({
    trigger: ".pin-section", start: "top top", end: "+=1500", pin: true, scrub: 1
  });
  ```
- **Tier fit:** T2 (short pins), T3 (multi-step pinned choreography).
- **Reduced-motion fallback:** don't pin — let the section scroll normally, keep
  any content changes as simple crossfades instead of scroll-scrubbed steps.
- **Perf note:** pinning forces layout recalculation on resize; always call
  `ScrollTrigger.refresh()` after dynamic content/image loads, and avoid pinning
  more than one section per viewport on mobile.

### Scroll-scrubbed animation
- **Good for:** tying an animation's progress directly to scroll position —
  product reveals, step-by-step diagrams, timeline scenes.
- **Tool:** GSAP ScrollTrigger `scrub: true` (or a number for smoothing lag).
- **Sketch:**
  ```js
  const tl = gsap.timeline({
    scrollTrigger: { trigger: ".reveal-product", start: "top top", end: "+=2000", scrub: 0.5, pin: true }
  });
  tl.to(".product", { rotateY: 360, scale: 1.2 }).to(".product-label", { opacity: 1 }, "<0.5");
  ```
- **Tier fit:** T2, T3.
- **Reduced-motion fallback:** drop scrub, either remove the sequence or replay it
  once as a short autoplay clip capped at ~600ms.
- **Perf note:** keep the scrubbed timeline to transform/opacity only — a
  scrubbed `filter` or layout property will visibly stutter since it re-runs on
  every scroll tick.

### Hover micro-interaction
- **Good for:** buttons, cards, links responding to pointer presence — the
  cheapest feedback signal in the vocabulary.
- **Tool:** CSS transitions (Tier 1) or Motion (Tier 2+, when it needs to
  coordinate with other component state).
- **Sketch (CSS):**
  ```css
  .btn { transition: transform 200ms ease-out, background-color 200ms ease-out; }
  .btn:hover { transform: translateY(-2px); }
  ```
- **Sketch (Motion):**
  ```jsx
  <motion.button whileHover={{ y: -2 }} whileTap={{ scale: 0.97 }} transition={{ duration: 0.2 }} />
  ```
- **Tier fit:** T1, T2, T3.
- **Reduced-motion fallback:** keep color/opacity feedback, drop the transform.
- **Perf note:** negligible cost either way; prefer CSS when there's no
  surrounding React state to coordinate, it avoids shipping JS for nothing.

### Magnetic button
- **Good for:** a button that subtly pulls toward the cursor within its bounds —
  signature Tier 3 interaction-design flourish.
- **Tool:** GSAP `quickTo` + a `mousemove` listener.
- **Sketch:**
  ```js
  const xTo = gsap.quickTo(btn, "x", { duration: 0.3, ease: "power3" });
  const yTo = gsap.quickTo(btn, "y", { duration: 0.3, ease: "power3" });
  btn.addEventListener("mousemove", (e) => {
    const r = btn.getBoundingClientRect();
    xTo((e.clientX - r.left - r.width / 2) * 0.35);
    yTo((e.clientY - r.top - r.height / 2) * 0.35);
  });
  btn.addEventListener("mouseleave", () => { xTo(0); yTo(0); });
  ```
- **Tier fit:** T3.
- **Reduced-motion fallback:** don't attach the listener at all; render a normal
  hover state.
- **Perf note:** `quickTo` is built for exactly this — it reuses a single tween
  and interpolates targets instead of creating a new tween per mousemove event,
  which is the difference between smooth and janky here. Never `gsap.to()` inside
  a raw mousemove handler.

### Custom cursor
- **Good for:** replacing the system cursor with a custom element that trails or
  reacts to hover targets — Tier 3 signature move for immersive/portfolio sites.
- **Tool:** GSAP `quickTo`.
- **Sketch:**
  ```js
  const cx = gsap.quickTo("#cursor", "x", { duration: 0.15, ease: "power3" });
  const cy = gsap.quickTo("#cursor", "y", { duration: 0.15, ease: "power3" });
  window.addEventListener("mousemove", (e) => { cx(e.clientX); cy(e.clientY); });
  ```
- **Tier fit:** T3.
- **Reduced-motion fallback:** never replace the system cursor — skip this
  technique entirely rather than degrade it; also skip on touch devices (no
  cursor to replace).
- **Perf note:** same `quickTo` reasoning as magnetic button; also `will-change:
  transform` on the cursor element, and make sure it's `position: fixed` outside
  normal layout flow so it never triggers reflow.

### Text-reveal / kinetic type
- **Good for:** headlines that animate in by character/word/line — hero
  statements, section headers.
- **Tool:** GSAP SplitText (now free).
- **Sketch:**
  ```js
  const split = SplitText.create(".headline", { type: "lines,words" });
  gsap.from(split.words, { opacity: 0, y: 20, stagger: 0.03, duration: 0.6, ease: "power2.out" });
  ```
- **Tier fit:** T2, T3.
- **Reduced-motion fallback:** render the full text immediately, no split/stagger
  — split text specifically should never run under reduced motion, it's the
  purest "decorative" case in this list.
- **Perf note:** call `split.revert()` on unmount/route change in SPA contexts to
  restore original DOM and avoid leaking wrapped spans; splitting long paragraphs
  (not just headlines) generates a lot of DOM nodes — reserve for short headline
  text.

### Page / route transition
- **Good for:** smooth visual continuity between pages instead of a hard cut.
- **Tool:** View Transitions API (native; Astro has it built in via
  `<ClientRouter />`) for MPA sites; Motion `AnimatePresence` for SPA/React-Router
  contexts.
- **Sketch (Astro/native):**
  ```astro
  ---
  import { ClientRouter } from "astro:transitions";
  ---
  <head><ClientRouter /></head>
  <main transition:animate="slide">...</main>
  ```
- **Sketch (Motion/SPA):**
  ```jsx
  <AnimatePresence mode="wait">
    <motion.div key={route} initial={{ opacity: 0 }} animate={{ opacity: 1 }} exit={{ opacity: 0 }} transition={{ duration: 0.2 }} />
  </AnimatePresence>
  ```
- **Tier fit:** T1 (native View Transitions, no JS cost), T2, T3 (Motion, for
  app-like SPA sections).
- **Reduced-motion fallback:** View Transitions API respects
  `prefers-reduced-motion` automatically when the transition CSS is gated behind
  the media query; for Motion, drop to an instant `duration: 0` crossfade.
- **Perf note:** native View Transitions cost effectively nothing extra (browser-
  compositor driven); Astro's MPA transitions degrade gracefully in Firefox
  (cross-document gap) — verify the fallback isn't a broken half-state, just no
  transition.

### WebGL / shader background
- **Good for:** hero backgrounds, ambient scenes that need to feel alive — the
  most expensive technique in the vocabulary, reserve for moments that earn it.
- **Tool:** React Three Fiber + a GLSL fragment shader (or a pre-built shader
  package like Paper Shaders for common effects without writing GLSL by hand).
- **Sketch:**
  ```jsx
  function ShaderPlane() {
    const mat = useRef();
    useFrame((state) => { mat.current.uniforms.uTime.value = state.clock.elapsedTime; });
    return (
      <mesh scale={[viewportW, viewportH, 1]}>
        <planeGeometry />
        <shaderMaterial ref={mat} vertexShader={vert} fragmentShader={frag}
          uniforms={{ uTime: { value: 0 } }} />
      </mesh>
    );
  }
  ```
- **Tier fit:** T3 ONLY.
- **Reduced-motion fallback:** freeze the shader on first frame (stop the
  `uTime` update loop) rather than removing it, or swap to a static gradient
  image entirely for `prefers-reduced-motion: reduce`.
- **Perf note:** always ship a mobile-simplified fallback — either a lower-res
  render target, a reduced shader (fewer octaves/iterations), or a static image
  below a viewport-width breakpoint. WebGL shader backgrounds are the single
  biggest mobile battery/thermal cost in this vocabulary; never ship the
  desktop-tuned version unconditionally to mobile.

## Per-tier motion budget

- **Tier 1 — CSS-only.** Hover transitions, native smooth-scroll
  (`scroll-behavior: smooth`), fluid type via `clamp()`, `@starting-style` for
  entry transitions on newly-shown elements. No JS animation library.
- **Tier 2 — Motion + optional Lenis + GSAP ScrollTrigger** for reveals and
  parallax. Decorative-JS budget: **≤ 60KB** shipped (mirrors the shared stack's
  decorative-JS budget rule — this is the same ceiling, not a separate one).
- **Tier 3 — full GSAP timeline choreography + R3F + shaders** + custom
  cursor/magnetic buttons, WITH a mobile-simplified fallback (reduced shader
  complexity, no custom cursor on touch, simplified or removed pin sequences
  below a breakpoint).

`prefers-reduced-motion` AND `prefers-reduced-transparency` must be honored
everywhere, at every tier — glass/blur effects need the transparency fallback as
much as animated effects need the motion fallback.
