# Context Adaptation

A standalone SVG piece is authored once and then *ships* somewhere. Where it lives — and what format it exports to — changes duration, amplitude, density, and which channels are even safe to use.

## Use-Context Scaling

| Where it lives | Duration | Amplitude | Density | Notes |
|----------------|----------|-----------|---------|-------|
| In-product micro-icon (16–48px) | 300–800ms | Generous (small render eats subtlety) | 1–2 channels | No fine detail; readable at size |
| App loader / status | 800–1500ms/cycle | Low–medium | Few elements | Seen constantly → calm, seamless loop |
| Marketing hero | 1500–4000ms | Full, layered | Primary + secondary + ambient | Seen once → can be dramatic |
| Social / video export | 2000–6000ms | Full | Rich, but legible on mute | Baked; no interactivity survives |
| Decorative ambient loop | 3000–8000ms | 10–20% of primary | Sparse, slow | Must read on the 100th loop |

Rules of thumb:
- **Smaller render → fewer channels, bigger amplitude.** Subtle motion vanishes at icon size; a 2% pulse is invisible at 24px.
- **Seen-once → richer; seen-always → calmer.** A splash reveal can show off. A loader that plays every session must never grate.
- **Loop-forever → restraint + seam.** Low amplitude, gentle sine, and start pose = end pose so the repeat is invisible.

## prefers-reduced-motion

Embedded SVGs should honor it. Reduced motion is not "no motion" — it is *calm* motion.

| Full version | Reduced variant |
|--------------|-----------------|
| Slide / scale entrance | Opacity fade only |
| Overshoot / bounce land | Simple ease-out, no spring |
| Continuous rotation loop | Static, or slow opacity pulse |
| Large auto-playing hero loop | Hold a still final pose |
| Multi-part staggered build | Single fade of the whole |
| Particle / drift ambient | Static, or one faint opacity breath |

Reduced means: drop spatial travel, keep opacity, kill spring, cut duration ~50%, and never auto-play a big continuous loop. Avoid vestibular triggers even in the full version — large-scale zoom, spinning elements >100px, rapid direction reversals.

## Export-Target Awareness

The same authored piece exports differently. Design for the lowest-common-denominator target you'll ship to.

| Target | Survives | Watch out for |
|--------|----------|---------------|
| Animated SVG | Everything: transform, opacity, stroke, path morph, filters, blends | Heaviest channels are fine but cost render; keep element counts sane |
| Lottie | transform, opacity, stroke draw, path morph | Feature limits — many SVG filters, blend modes, and some masks don't translate; test the morph |
| Video / GIF | The final look, baked frame-by-frame | No transparency in GIF-with-matte edge cases; loop seam is locked in; file size scales with duration + canvas |

- **If it might become Lottie:** favor transform + opacity + stroke.dashOffset + shape.path. Avoid filter-driven glow, blend modes, and complex clip stacks — rebuild those as real shapes.
- **If it might become video/GIF:** the loop seam and timing are permanent; get them right before export. Mind transparency and total weight.

## Performance & Weight Sense

Not a live-UI paint budget — just craft economy so the file stays light and the morph stays smooth.

- **Favor transform + opacity.** They're the cheapest and translate everywhere.
- **shape.path morphs and filters are heavier.** Use them where they earn their keep, not as default polish.
- **Keep element counts reasonable.** Fewer, larger particles read better than a swarm of tiny ones and export lighter.
- **Stagger over simultaneous.** Spreading motion in time keeps any single frame simple.

## Content-Type → Personality

| Subject | Personality | Duration | Motion Density |
|---------|-------------|----------|---------------|
| Fintech / banking mark | Corporate / Premium | 250–500ms | Low |
| Social sticker / emoji | Playful | 150–400ms | High |
| Enterprise SaaS icon | Corporate | 200–400ms | Low |
| Gaming / esports | Energetic | 100–250ms | High |
| Health / wellness | Premium / Calm | 300–600ms | Very low |
| E-commerce / retail | Varies | 200–400ms | Medium |
| Editorial / luxury | Premium | 350–600ms | Low |
| Kids / education | Playful | 150–350ms | High |

See [motion-personality.md](motion-personality.md) for how each personality sets easing and overshoot.
