# Entrance & Exit Patterns

The build-on (intro) and build-off (outro) beats of a self-contained piece or a multi-beat sequence. A reveal is how a mark, icon, or scene *arrives*; an exit is how a beat clears before the next one. These play on load — they are not reactions to input.

Easing in CSS notation; named-curve → value in [../reference/timing-easing.md](../reference/timing-easing.md).

## Entrance Strategies (build-on)

### 1. Slide In
- `transform.translate` + `compositing.opacity`; offset 20–40px + opacity 0 → home + opacity 1
- Easing: ease-out; 200–350ms

| Personality | Offset | Easing | Overshoot (y past 1) |
|------------|--------|--------|-----------|
| Playful | 30–50px | (0.34, 1.4, 0.2, 1) | 10–15% |
| Premium | 15–25px | (0.4, 0, 0.2, 1) | 0% |
| Corporate | 20–30px | (0.2, 0, 0, 1) | 0–3% |
| Energetic | 40–80px | (0.05, 0.7, 0.1, 1) | 15–25% |

Direction carries meaning: from below = arrival/growth, from right = forward, from left = back, from above = authority/drop.

### 2. Scale In
- `transform.scale` + opacity; start 85–95% + opacity 0 → 100% + opacity 1
- **Never from 0.** Nothing in the world appears from nothing — a `scale(0)` entry looks like a teleport. Start at ~0.9 so the shape already has a body as it moves; Playful/Energetic can start lower for a bigger pop, but still never at 0.
- Set `transform.origin` deliberately: center for a pop, an edge to hinge/anchor
- 250–400ms

| Personality | Start Scale | Easing | Overshoot |
|------------|------------|--------|-----------|
| Playful | 70–80% | (0.34, 1.4, 0.2, 1) | 10–20% |
| Premium | 95–98% | (0.4, 0, 0.2, 1) | 0% |
| Corporate | 90–95% | (0.2, 0, 0, 1) | 0–3% |
| Energetic | 50–70% | (0.05, 0.7, 0.1, 1) | 15–30% |

Best for: logo marks, badges, emoji/stickers, icon pop-ins.

### 3. Clip / Mask Reveal
- Wipe with a mask or clip + opacity; 300–500ms, ease-out
- Directions: top-to-bottom (dramatic), left-to-right (reading order), center-out (focus), edge-in (contained)
- Best for: wordmarks, banners, illustration panels emerging behind a wipe.

### 4. Stroke Draw-On
- `stroke.dashOffset` from full length → 0 reveals a line as if drawn; 400–900ms, ease-out
- Then `fill.opacity` 0 → 1 to fill the shape once the outline lands (dashOffset + fill.opacity combo)
- Best for: line-art icons, signatures, outlined logos, connector paths.

### 5. Assembled Build (Multi-Part)
- Parts arrive from different positions/scales; stagger 50–100ms; total 300–600ms
- Best for: icon assembly, logo builds where letters/shapes converge, illustration elements populating a scene, data-viz bars rising in.
- See [multi-element.md](multi-element.md) for the choreography.

## Exit Strategies (build-off)

**Rule**: exits run at 65–75% of the matching entrance. Departures deserve less time than arrivals.

### 1. Slide Out
- Offset 20–40px + opacity 0; ease-in (0.4, 0, 1, 1); 150–250ms

### 2. Dissolve Out
- Opacity → 0 (optional scale to 98%); ease-in; 150–250ms
- Best for: gentle departures, cross-dissolves between beats, backgrounding.

### 3. Collapse Out
- Scale 85–95% + opacity 0; ease-in; 150–250ms
- Best for: an element retracting, a mark folding away before the next beat.

### 4. Draw-Off (Erase)
- `stroke.dashOffset` 0 → full length un-draws the line; ease-in; 200–400ms
- Best for: undoing a signature, dissolving a connector, reversing a line-art reveal.

## Entrance–Exit Continuity (multi-beat pieces)
- The eye should follow naturally from one beat's exit to the next beat's entrance.
- Exit an element near where the next enters when possible.
- Overlap exit and entrance by 100–150ms so beats feel woven, not stitched.
- Same easing family across a paired build-on / build-off.

## Recipes

### Logo Mark Assembles
1. Parts scale/slide in from spread positions, stagger 60–80ms (250ms each, ease-out)
2. Overshoot on land (playful 10–15%, corporate 0–3%)
3. Wordmark strokes draw on (dashOffset, 400ms, 100ms after mark settles)
4. Ambient glow pulse begins once everything has landed

### Icon Draws On
1. Outline draws via dashOffset (500ms, ease-out)
2. Fill fades in (fill.opacity, 200ms, starting ~350ms)
3. Tiny scale settle 102% → 100% (120ms) for a breath of life

### Illustration Scene Builds In
1. Background/stage fades or clip-reveals first (400ms)
2. Midground elements slide/scale in, staggered (60–100ms apart)
3. Hero subject lands last with the most overshoot
4. Ambient layer (drift, shimmer) starts after the build settles

### Beat-to-Beat Handoff
1. Outgoing beat dissolves or collapses (70% of its entrance time, ease-in)
2. Incoming beat enters overlapping by 100–150ms
3. Any shared element morphs across (shape.path or translate, ease-in-out) instead of exiting and re-entering
