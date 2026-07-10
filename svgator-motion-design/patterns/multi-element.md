# Multi-Element Patterns

How several shapes move *together* — the choreography of a mark, a scene, or an explainer beat. Stagger, sequence, and counter-motion turn a pile of shapes into one coordinated piece. All authored to play on load or loop; no dragging, no tabs, no clicks.

Easing in CSS notation; named-curve → value in [../reference/timing-easing.md](../reference/timing-easing.md). Deeper principles in [../director/choreography.md](../director/choreography.md).

## Stagger Recipes

Never move everything at once. A cascade reads; a simultaneous pop is a blur.

### Icon Parts / Logo Letters
- Each part slides or scales in + opacity (200–250ms, ease-out); stagger 40–80ms; total < 500ms
- Reading order (left→right, or center→out); last part gets the most overshoot

| Personality | Per-part duration | Stagger | Easing |
|------------|---------|---------|--------|
| Playful | 250ms | 60ms | (0.34, 1.4, 0.2, 1) |
| Premium | 350ms | 80ms | (0.4, 0, 0.2, 1) |
| Corporate | 200ms | 50ms | (0.2, 0, 0, 1) |
| Energetic | 150ms | 30ms | (0.05, 0.7, 0.1, 1) |

### Illustration Elements Populate a Scene
- Elements scale from ~90% + fade (250ms, ease-out); stagger 60–100ms
- Build back-to-front: stage → midground → hero subject last
- Alt orders: center-out (focus), bottom-up (growing), random-ish (organic scatter)

### Data-Viz Bars / Segments
- Bars grow via `transform.scale` on a bottom `transform.origin` (or a clip wipe), 250–350ms, ease-out
- Stagger 50–80ms in data order; a value label fades in ~50ms after each bar lands
- Lines draw on with `stroke.dashOffset`; pie/donut segments sweep via dashOffset around the arc

### Sequenced Build (timeline sketch)
```
0ms   — Stage/background clip-reveals (400ms)
150ms — Midground elements begin (250ms each, 80ms stagger)
450ms — Hero subject lands with overshoot (300ms)
650ms — Secondary details (labels, sparkles) fade in
800ms — Ambient layer (drift, shimmer) begins
```

## Coordinated Sequences

### Multi-Beat Explainer
Beat A plays → dissolves (70% of its entrance, ease-in) → Beat B enters overlapping by 100–150ms. Shared elements morph across (`shape.path` or translate, ease-in-out) rather than exiting and re-entering. Keep one hero motion per beat.

### Scene Reveal
0ms: stage clip-reveals (400ms) → 150ms: midground staggers in (80ms apart) → 450ms: hero subject scales in with overshoot → 650ms: labels/accents fade in reading order → 800ms: ambient drift starts.

### Logo Lockup
Mark assembles from spread parts (stagger 60–80ms) → mark settles with overshoot → wordmark strokes draw on (dashOffset, 100ms after mark) → tagline fades up last → ambient glow pulse begins.

### Looping Ensemble
Elements cycle on offset phases (different durations prevent sync) so the group breathes continuously; the whole loop's start pose equals its end pose. See [ambient-continuous.md](ambient-continuous.md).

## Choreography Rules

### Timing Overlap
How much a next element starts before the previous finishes:
`0% = methodical` | `25% = brisk (standard)` | `50% = fluid` | `75% = rapid (energetic)`

### Group Consistency
- Same easing family across the group; different durations/delays are fine
- Exception: the secondary/ambient layer may use its own easing

### Shared Origin
Motion radiates from a trigger point (where the mark "starts" or where a burst originates): closer elements move first, farther elements get more delay. Assembles, bursts, and ripples all read from a shared origin.

### The 1/3 Rule
No element travels more than 1/3 of the canvas without an intermediate keyframe — a direction change, speed shift, or arc. Applies per element in a cascade, not just the hero. (See [../director/core-philosophy.md](../director/core-philosophy.md).)

### Counter-Motion

| Hero does | Counter-motion |
|-----------|---------------|
| Slides right | Background drifts left (20–30%) |
| Scales up | Cast shadow spreads + softens |
| Lifts up | Shadow drops + fades |
| Rotates CW | Ambient element rotates CCW |
| Expands / bursts | Siblings compress inward slightly |

Counter-motion runs simultaneously with the hero and sells weight and space.

### Attention Budget
Max 2–3 elements in active primary motion at once; ambient doesn't count. Stagger rather than synchronize so the eye always has one clear thing to follow.
