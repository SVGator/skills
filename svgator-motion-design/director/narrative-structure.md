# Narrative Structure

Every piece tells a tiny story, even inside 800ms: something gathers, something happens, the world reacts, it settles. Skip an act and the motion feels like it started late or stopped early. Here's the arc, and how it compresses as the clock shrinks.

## The four acts

### Act 1 — Anticipation (10–20%)
The wind-up that makes the payoff land. The eye needs to feel it coming.
- Wind-up: a small move *opposite* the main direction.
- Gathering: shapes pull together before they disperse.
- Dimming: context fades so the focus is clear. Tension: hold the compressed pose ~50ms.
- Skip it under 150ms — no room to wind up.

### Act 2 — Action (30–50%)
Peak energy — the one communicative move the whole piece is about. Its character is set by what the piece *is*:
- Fast + direct (sharp easing) → alert/warning icons.
- Smooth + flowing (gentle easing, curves) → logo reveals.
- Explosive + expanding (`ease-out-expo`, radial) → celebration bursts.
- Controlled + precise (near-linear) → data/chart draw-ons.

### Act 3 — Reaction (10–20%)
The world answering the action — this is what separates a designed scene from a lone tween.
- Cast shadows adjust 50–100ms after primary.
- Sibling shapes shift 50–150ms after primary.
- Environment/particles ripple 100–200ms after primary.
- Counter-motion runs simultaneously with the action.
- Skip it for a simple single-shape beat.

### Act 4 — Resolution (20–30%)
The landing. Where a piece earns the word *finished*.
- Overshoot settle (a back-easing bezier); `compositing.opacity` reaches its final value on ease-out.
- 100–200ms of breathing room before it loops or moves on.
- Even 50ms of settling changes the whole feel — the difference between *stopped* and *arrived*.

## Compressing the acts to fit the clock

The shorter the piece, the more acts you drop — the action always survives, the trimmings go first.

| Total | Anticipation | Action | Reaction | Resolution |
|-------|--------------|--------|----------|------------|
| 100–200ms | skip | 60–70% | skip | 30–40% |
| 200–400ms | 10–15% | 40–50% | 10–15% | 25–30% |
| 400–800ms | 15–20% | 30–40% | 15–20% | 20–25% |
| 800ms+ | 20% | 30–35% | 15–20% | 25–30% |

## Stringing beats together

When a piece has several beats, the join between them sets the feel: overlap them for fluidity, sequence them for clarity, run them in parallel for energy.

Three progressions cover most pieces:
- **Build-up**: low → rising → peak → settling.
- **Cycle**: depart → peak → return → repeat — the natural shape of a seamless loop, because the end pose *is* the start pose.
- **Impact**: sudden action → ripple → slow settle.

## The arc by personality

Same four acts, four different accents. Personality shows most in how a piece winds up and how it lands.

| Personality | Anticipation | Action | Resolution |
|-------------|--------------|--------|------------|
| Playful | exaggerated wind-up | bouncy, overshoot | wobble settle |
| Premium | subtle tension | smooth, controlled | elegant ease |
| Corporate | minimal / none | direct, efficient | clean stop |
| Energetic | quick gather | explosive | fast snap |

## Ready-made shapes

- **Reveal**: tension (dim, `scale` 95%) → emerge (100%, full opacity) → surroundings adjust → settled.
- **Departure**: gather (`scale` 98%) → exit → the gap closes → the scene settles.
- **Transformation**: destabilize (a vibration) → morph (`shape.path`) → a secondary detail appears → the new state breathes.
- **Celebration**: compress (50–100ms) → burst (`scale` + particles) → settle → rest on the positive state.
