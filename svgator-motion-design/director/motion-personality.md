# Motion Personality

Personality comes off the *asset and its brand* — what the piece **is**. A bouncy mascot, an elegant logo reveal, a utility icon, and a punchy loader want four different hands. Read it off the artwork, then hold it across every element so the set feels like one designer made it.

## Four archetypes

### Playful

Motion that grins — it overshoots, wobbles, and lands with a bounce. The joy is in the exaggeration.

| Trait | Value |
|-------|-------|
| Duration | 150–300ms |
| Easing | ease-out-back / bouncy beziers |
| Overshoot | 10–20% |
| Paths | arcs and curves, never straight |
| Squash-stretch | yes, on impacts |

Signature: bounce-and-settle, squash on landing, `transform.rotate` wobble, bright `fill.paint` pops, varied stagger.
Use for: mascots, stickers, character animation, casual-game assets, emoji reactions, celebratory badges, kids' illustration.

### Premium / Luxury

Restraint is the whole point. Slow, clean, no bounce — it says *expensive* by refusing to rush or show off.

| Trait | Value |
|-------|-------|
| Duration | 350–600ms |
| Easing | cubic-bezier(0.4, 0, 0.2, 1) |
| Overshoot | 0% |
| Paths | smooth curves, subtle parallax |
| Squash-stretch | never |

Signature: slow fades, a barely-there scale (98%→100%), generous held pauses, two channels at most (`compositing.opacity` + one), an ultra-smooth `stroke.dashOffset` draw-on.
Use for: elegant logo reveals, fashion/finance/jewellery marks, editorial illustration, monogram animation, refined line art.

### Corporate / Professional

Motion you trust because it's predictable. Nothing surprising, nothing wasted — it just works, consistently, every time.

| Trait | Value |
|-------|-------|
| Duration | 200–400ms |
| Easing | cubic-bezier(0.2, 0, 0, 1) |
| Overshoot | 0–3% |
| Paths | mostly straight, small arcs for emphasis |
| Squash-stretch | no |

Signature: consistent timing, clear transitions, functional moves, uniform stagger.
Use for: technical/utility icon sets, infographic beats, explainer diagrams, enterprise logo animation, healthcare/banking marks.

### Energetic / Dynamic

Motion with adrenaline — fast, big, diagonal, overshooting hard. It hits before you're ready and that's the point.

| Trait | Value |
|-------|-------|
| Duration | 100–250ms |
| Easing | ease-out-expo / elastic |
| Overshoot | 15–30% |
| Paths | dramatic arcs, large displacement, diagonal |
| Squash-stretch | yes, exaggerated |

Signature: big `transform.scale` swings (50–150%), fast color transitions, particle bursts, accelerating stagger, entrances snapping in from the edge.
Use for: sports/gaming/music marks, punchy loaders, event stingers, fitness icons, hype logo stings.

## Reading it off keywords

When the brief hands you words, they point at an archetype. When it hands you nothing, the subject decides.

| Keywords | Archetype |
|----------|-----------|
| fun, whimsical, bouncy, cute, friendly, mascot | Playful |
| elegant, minimal, luxury, sophisticated, refined | Premium |
| clean, professional, technical, utility, explainer | Corporate |
| dynamic, energetic, bold, exciting, punchy | Energetic |
| (unspecified) + utility/technical icon | Corporate (default) |
| (unspecified) + character/illustration | Playful (default) |

## A recognizable signature

Consistency is what makes a set feel authored by one hand. Lock three constants and hold them.

### 1. Signature easing (80% of keyframes)
Playful: ease-out-back · Premium: cubic-bezier(0.4, 0, 0.2, 1) · Corporate: cubic-bezier(0.2, 0, 0, 1) · Energetic: ease-out-expo

### 2. Duration palette

Three tiers you reuse instead of inventing a new number each time — that reuse is what reads as intentional.

| Tier | Playful | Premium | Corporate | Energetic |
|------|---------|---------|-----------|-----------|
| Quick | 150ms | 350ms | 200ms | 100ms |
| Standard | 250ms | 500ms | 300ms | 180ms |
| Slow | 400ms | 800ms | 450ms | 300ms |

### 3. Entrance pattern
Playful: bounce up from below · Premium: slow fade + scale 98%→100% · Corporate: slide + opacity · Energetic: snap in from the edge + overshoot

## Mixing archetypes

- Keep 90% in the primary archetype; let a single moment borrow another.
- Ease into a personality shift, never snap between them.
- Example: a corporate explainer icon borrows Playful for its success/confirm beat only — one moment of warmth in an otherwise even piece.
