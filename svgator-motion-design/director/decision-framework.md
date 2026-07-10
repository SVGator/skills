# Decision Framework

Going from "animate this logo" to actual channels, timings, and curves. The piece plays on load or loops — nobody drives it — so every choice serves *reading*, not reacting.

## The first questions

### 1. What's it for?

The purpose sets the whole approach before anything else. Say what the motion is *doing* and the priority falls out of it.

| Purpose | The approach | What it lives or dies on |
|---------|--------------|--------------------------|
| Reveal a mark/icon/scene | build-on: `stroke.dashOffset` draw, scale-in, clip reveal | clarity — you must read what it is |
| Emphasize one element | scale pulse, color shift, wobble | legibility — the eye lands on the right thing |
| Transform / morph | `shape.path`, staged swap | continuity — no jump-cut between states |
| Loop as a living accent | slow, seamless, low amplitude | subtlety — it can't grate on repeat |
| Land a feedback beat | overshoot pop + burst, or shake + flash | punch — it has to feel like something happened |

### 2. Who watches it, and how often?

How many times an eye meets a piece decides how loud it's allowed to be. A hero seen once can shout; a loader seen every session has to whisper.

- Seen once (hero reveal, splash) → dramatic, longer, richer is fine.
- Seen every session (loader, status icon) → subtle, fast, calm.
- Seen on the 100th loop (ambient decoration) → low amplitude, invisible seam, nothing that nags.
- Calm setting (reading, dashboard) → gentle. Celebratory setting (an onboarding win) → let it be exuberant.

### 3. Where does it ship?

The frame the piece plays in constrains what it can carry. A 24px icon can't hold layered choreography; a hero canvas can.

- Tiny render (16–48px icon) → few channels, generous amplitude, no fine detail that'll vanish.
- Large hero canvas → layered choreography, secondary + ambient earn their place.
- Busy surrounding layout → simpler, one hero move. Empty stage → it can carry more.
- Loops forever vs. plays once → forever demands a seamless start=end pose and real restraint.

See [context-adaptation.md](context-adaptation.md) for the where-it-lives specifics.

## Four levels, in order

### Level 1 — Motion category

What *kind* of move this is. It scopes the channels before you pick among them.

| Category | When | Channels it reaches for |
|----------|------|-------------------------|
| Revealing | a mark/icon/scene appears (build-on) | `stroke.dashOffset`, `transform.scale`, clip, `compositing.opacity` |
| Emphasizing | pull the eye to one element | scale pulse, `fill.paint`, small `transform.rotate` |
| Transitioning / morphing | one thing becomes another | `shape.path`, staged opacity swap |
| Ambient | continuous living accent, loops | slow `translate`/`rotate`, opacity, shimmer |
| Feedback beat | a self-playing success/error/loading moment | scale + burst, shake + color, rotation loop |

There's no "responding" category — nothing reacts to input. A feedback beat is *authored* to play on its own, not fired by a click.

### Level 2 — Personality

Match it to the brand and the subject. Personality sets the overshoot budget, the amplitude, and the easing family before you touch a keyframe. → [motion-personality.md](motion-personality.md)

### Level 3 — Direction

Which way a thing moves is already saying something. Choose the direction that agrees with the message instead of fighting it.

| Direction | What it says |
|-----------|--------------|
| Upward | growth, aspiration, lift |
| Downward | settling, completion, grounding |
| Rightward | progression, arrival |
| Leftward | regression, departure |
| Outward (scale up) | importance, emergence |
| Inward (scale down) | dismissal, recede |
| Center-seeking | focus, convergence, assembly |
| Center-fleeing | distribution, release, burst |

### Level 4 — Channels

Pick the channel that *carries the meaning*, not just the one that happens to move. Two is the sweet spot: primary carries the meaning, secondary adds the polish. → [property-meaning.md](../reference/property-meaning.md)

## The quick path

```
1. PURPOSE → what is this piece FOR?
   ├── Reveal    → build-on: draw / scale-in / clip, ease-out, personality-matched
   ├── Emphasize → scale or color pulse on one element
   ├── Morph     → shape.path with matched node counts
   ├── Loop      → slow, sine, seamless seam, low amplitude
   └── Moment    → success (pop + burst) or error (shake + flash), self-playing

2. PERSONALITY → match keywords → sets amplitude + overshoot budget
   ├── Fun/bouncy      → Playful (y ~1.2–1.4)
   ├── Elegant/luxury  → Premium (no overshoot)
   ├── Clean/pro       → Corporate (y ≤ ~1.05)
   └── Bold/dynamic    → Energetic (y ~1.4–1.55)

3. CHANNELS → the minimum that carries meaning (two = sweet spot)

4. TIMING → duration by type; scale for distance, weight, render size

5. EASING → build-on = ease-out · morph/travel = ease-in-out ·
            loop = sine · spin/progress = linear · land = overshoot bezier
```

Named-curve → value table in [../reference/timing-easing.md](../reference/timing-easing.md).

## Before you call it done

Walk it once against what it was for. Each line is a way the piece can quietly fail.

| Check | The question |
|-------|--------------|
| Purpose | does the motion say what the piece is for? |
| Personality | does it match the brand and subject? |
| Repetition | still fine on the 100th loop? (loops only) |
| Seam | loop start pose = end pose, no visible jump? |
| Layers | primary + secondary + ambient, not primary alone? |
| Timing | right duration for the type and the render size? |
| Settle | a beat of stillness before it loops or ends? |
