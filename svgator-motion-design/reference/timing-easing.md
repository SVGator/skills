# Timing & Easing — for SVGator

SVGator easing is **per keyframe**, and governs the segment from that keyframe to the next. Types: `linear`, `cubic-bezier`, `steps`. This file converts the named curves you reason with into the `{from:{x,y}, to:{x,y}}` SVGator wants.

## Cubic-bezier cheat sheet (named curve → SVGator value)

A standard CSS `cubic-bezier(x1,y1,x2,y2)` maps to `{ "from": {"x":x1,"y":y1}, "to": {"x":x2,"y":y2} }`. **x is clamped 0..1; y is unbounded** (push y beyond 1 for overshoot).

| Curve | CSS | SVGator `value` |
|-------|-----|-----------------|
| ease-out (entrance) | (0, 0, 0.2, 1) | `{"from":{"x":0,"y":0},"to":{"x":0.2,"y":1}}` |
| ease-in (exit) | (0.4, 0, 1, 1) | `{"from":{"x":0.4,"y":0},"to":{"x":1,"y":1}}` |
| ease-in-out (on-screen) | (0.45, 0, 0.55, 1) | `{"from":{"x":0.45,"y":0},"to":{"x":0.55,"y":1}}` |
| sine ease-in-out (ambient loop) | (0.37, 0, 0.63, 1) | `{"from":{"x":0.37,"y":0},"to":{"x":0.63,"y":1}}` |
| MD3 emphasized (attention entrance) | (0.05, 0.7, 0.1, 1) | `{"from":{"x":0.05,"y":0.7},"to":{"x":0.1,"y":1}}` |
| MD3 accelerate (dismiss) | (0.3, 0, 1, 1) | `{"from":{"x":0.3,"y":0},"to":{"x":1,"y":1}}` |
| snappy / decisive | (0.2, 0, 0, 1) | `{"from":{"x":0.2,"y":0},"to":{"x":0,"y":1}}` |
| gentle float | (0.4, 0, 0.2, 1) | `{"from":{"x":0.4,"y":0},"to":{"x":0.2,"y":1}}` |
| **back / overshoot** (playful land) | (0.34, 1.4, 0.2, 1) | `{"from":{"x":0.34,"y":1.4},"to":{"x":0.2,"y":1}}` |
| **elastic snap** (energetic) | (0.68, -0.55, 0.27, 1.55) | `{"from":{"x":0.68,"y":-0.55},"to":{"x":0.27,"y":1.55}}` |
| linear (spin/progress only) | — | `{"type":"linear","value":null}` |

**When the default feels weak.** The polite ease-out is fine for calm work, but a move meant to feel *intentional* wants a curve that snaps early and glides to a stop. Reach for these when crisp beats gentle:

| Curve | CSS | SVGator `value` |
|-------|-----|-----------------|
| strong ease-out (crisp arrival) | (0.23, 1, 0.32, 1) | `{"from":{"x":0.23,"y":1},"to":{"x":0.32,"y":1}}` |
| strong ease-in-out (decisive on-screen move) | (0.77, 0, 0.175, 1) | `{"from":{"x":0.77,"y":0},"to":{"x":0.175,"y":1}}` |
| drawer glide (long, smooth settle) | (0.32, 0.72, 0, 1) | `{"from":{"x":0.32,"y":0.72},"to":{"x":0,"y":1}}` |

A stronger curve reads *faster* at the same duration — the eye catches movement immediately, then a soft landing. And never `ease-in` for an arrival: it stalls at the exact instant the viewer is watching most closely, and the whole piece feels sluggish.

**Directional rule:** entrance → ease-out · exit → ease-in · on-screen/travel → ease-in-out · looping ambient → sine · continuous rotation/progress → linear. Never linear for spatial or scale motion.

**Overshoot the cheap way:** one keyframe with a `y > 1` bezier springs into place — no extra keyframe needed. For a controlled squash-then-settle, use 3 keyframes (start → overshoot pose → settle) with an eased middle segment (see the entrance recipe).

## Steps easing
`{"type":"steps","value":{"steps":N,"jump":0|1}}` — hard, mechanical stepping (typewriter reveals, ticking counters, choppy retro motion). `steps ≥ 1`.

## Duration by animation type (full timeline)

| Type | Duration |
|------|----------|
| Icon micro-anim | 300–800ms |
| Looping status icon | 1000–2000ms |
| Logo reveal | 1200–2500ms |
| Loader / spinner (per cycle) | 800–1500ms |
| Sticker / emoji | 600–1500ms |
| Illustration / explainer beat | 1500–4000ms |
| Hero / ambient loop | 3000–8000ms |

## Timing principles (medium-agnostic, still true)

- **Distance scales duration.** A shape crossing more of the canvas needs more time: ~100px unit = base; 200px ≈ 1.3×; full-canvas ≈ 1.8–2×.
- **Enter > exit.** Exits run at 65–75% of the matching entrance. Arrivals deserve more time than departures.
- **Weight → speed.** Heavy/large elements move slower with higher damping (no overshoot); light elements move fast and can overshoot.
- **Secondary trails primary** by 50–150ms with a different easing. Shadows, trailing parts, reactive elements arrive late — that offset is what makes it feel real.
- **Stagger budget < 500ms total.** Per-element delay 30–100ms (micro cascade 20–40, standard 50–100, dramatic 100–200). Beyond ~500ms the piece feels slow.

## Overshoot budget by personality

| Personality | Bezier `y` past 1 | Feel |
|-------------|-------------------|------|
| Premium | none (y ≤ 1) | pure, controlled |
| Corporate | ≤ ~1.05 | crisp, minimal spring |
| Playful | ~1.2–1.4 | bouncy, alive |
| Energetic | ~1.4–1.55 | punchy, exaggerated |

## Timeline phase split (setup → action → resolution)

| Total | Anticipation | Action | Resolution / settle |
|-------|-------------|--------|---------------------|
| ≤400ms | skip | 55–70% | 30–40% |
| 400–800ms | 10–15% | 40–50% | 25–35% |
| 800ms+ | 15–20% | 30–40% | 25–30% |

Even 50–100ms of settle at the end transforms the feel. Leave a beat of stillness before a loop repeats.
