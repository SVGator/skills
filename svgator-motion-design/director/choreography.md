# Choreography

When more than one thing moves, the danger is chaos — everything arriving at once, from everywhere, competing. Choreography is how you give a crowd a single read: one hero, a clear order, and motions that answer each other instead of fighting.

## Give the eye a hero

The eye can only follow one thing first. Pick it, and make everything else defer.

- The hero gets the largest displacement and the most attention-grabbing curve.
- Supporting shapes are subtler in every dimension — smaller travel, gentler easing, later entrance.

## One origin, one direction

Elements entering from mixed directions read as a scatter. Bring them from a shared edge or a common point and the group feels intentional instead of accidental.

## Counter-motion

A world that reacts feels alive. When the hero moves, something answers in the opposite direction at a fraction of the speed — that push-back is what sells weight and depth.

| Hero move | What answers | Speed of the answer |
|-----------|--------------|---------------------|
| enters from left | a background shape shifts right | 20–30% |
| scales up | its cast shadow scales down | 10–20% |
| rotates clockwise | an ambient element drifts counter-clockwise | 15–25% |
| lifts (Y up) | the shadow spreads and softens | 20–30% |

## The shape of the sequence

Even a multi-element scene has the same three acts as a single beat — establish, act, settle — just spread across a cast.

| Phase | Share of runtime | What happens |
|-------|------------------|--------------|
| Setup | 20–30% | elements enter, the scene establishes |
| Action | 30–40% | the primary motion, the hero moment |
| Resolution | 30–40% | settle, secondary reactions, breathing |

Leave 100–200ms of stillness after resolution before the loop repeats or the next motion starts — the pause is what lets the moment register.

## The two 1/3 rules

**Distance.** Nothing travels more than a third of the viewBox without a keyframe changing its direction, speed, or arc — a long constant-velocity slide reads as fake. Break it with a turn, a pace shift, or a curved path.

**Elements.** With three or more animated shapes, keep at most a third in motion at once. Stagger so shape 1 is settling as shape 3 starts — that overlap keeps the scene alive without crowding the eye.

## Stagger patterns

The order things arrive in *is* the choreography. Pick the pattern that matches the read you want.

| Pattern | How it flows | Best for |
|---------|--------------|----------|
| Sequential | reading order | icon rows, letter-by-letter wordmarks |
| Center-out | radiating from the middle | hero marks, burst rings |
| Random | varied timing | organic, particle-like scatter |
| Wave | sine-based offset | data bars, equalizers, dot loaders |
| Reverse | last-to-first | exits, rewind beats |

- Every staggered element shares one easing family — vary the start time, never the curve. Mixed curves read as several unrelated animations.
- Optional: give the last element a slight overshoot as punctuation.

## When a crowd reacts to one moment

Sometimes many shapes answer a single event. Keep them tied to it: they start together but needn't land together.

- All start within 50ms of each other.
- They can arrive at staggered times — a shared start, spread landings.
- Same easing family, motion radiating from one common point.

## Steering the eye

You can walk someone's attention across the frame with motion alone.

| Technique | How it works |
|-----------|--------------|
| Leading motion | animate the target *before* its context, so the eye's already there |
| Following motion | settle the motion on the focal point |
| Ambient motion | a subtle continuous drift/glow in the periphery, holding the edges alive |
| Pointing motion | a directional cue aimed at the key element |

### Depth through speed

Parallax is just speed difference. Move near things faster than far things and flat shapes gain layers.

| Layer | Displacement | Speed |
|-------|--------------|-------|
| Foreground | 1.0x | fastest |
| Midground | 0.5x | medium |
| Background | 0.2x | slowest |

## Worked recipes

### Logo reveal
1. Backdrop shape fades in (100ms).
2. Hero mark scales 95%→100% + fades (250ms, ease-out, 100ms delay).
3. Wordmark letters stagger in (50ms between, 200ms each).
4. Underline draws on via `stroke.dashOffset` (300ms, starts with the letters).
5. An ambient glow pulses on the mark, landing last.

### Icon draw-on
1. Container/base shape fades in (200ms).
2. Outline strokes draw on via `stroke.dashOffset` (300ms, 50ms delay).
3. `fill.opacity` rises after the outline lands (200ms, 100ms after the stroke).
4. Accent detail last (150ms).

### List / grid build (staggered items)
1. Items fade + slide from below (200ms each, ease-out).
2. 50ms stagger between items, in reading order.
3. A subtle 3–5% scale overshoot as each one lands.
