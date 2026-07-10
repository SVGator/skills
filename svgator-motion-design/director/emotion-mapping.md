# Emotion-to-Motion Mapping

Decide what it should make someone feel, then let the feeling pick the curve, the path, and the pace. This is the translation table from emotion to motion — start here, before any channel.

## The core mapping

Each feeling has a native way of moving. Joy arcs upward and overshoots; sadness droops and drags. Match the motion to the emotion and it reads without anyone having to think.

| Emotion | How it moves | Path | Easing | Duration |
|---------|--------------|------|--------|----------|
| Joy / Delight | bouncy, arcs, overshoots | curved, upward | ease-out-back | 200–400ms |
| Calm / Serenity | smooth, flowing, unhurried | gentle curves | sine ease-in-out | 500–1000ms |
| Urgency / Alert | sharp, fast, no wind-up | straight lines | ease-out | 100–200ms |
| Sadness / Weight | slow, sinking | drooping curves | cubic ease-in-out | 600–1200ms |
| Surprise / Impact | sudden, expanding | radial outward | ease-out-expo | 150–300ms |
| Elegance / Grace | slow, controlled | long smooth arcs | cubic-bezier(0.4, 0, 0.2, 1) | 400–700ms |
| Playfulness | bouncy, irregular | arcs, squiggly | ease-out-back | 200–350ms |
| Confidence | direct, decisive | straight, horizontal | ease-out | 200–400ms |
| Curiosity | exploratory, varied | mixed, circular | varied | 300–500ms |
| Tenderness | soft, gentle | very subtle curves | soft ease-in-out | 600–1000ms |

## The path itself carries emotion

*Where* a shape travels speaks before it arrives. A sharp angle feels tense; a smooth curve relaxes. Route the `transform.translate` path to say what you mean.

| Path shape | What it feels like |
|------------|--------------------|
| Angular / sharp | tense, urgent, mechanical |
| Curved / smooth | relaxed, friendly, organic |
| Spiral | playful, whimsical |
| Straight diagonal | dynamic, purposeful |
| Vertical up | growth, achievement |
| Vertical down | settling, gravity |
| Horizontal | journey, progress |
| Radial outward | explosion, release |
| Radial inward | focus, convergence |

## Intensity — how loud to feel it

The same emotion can whisper or shout. Match the intensity to how often and how loudly the piece is meant to be seen.

| Intensity | What it looks like | When |
|-----------|--------------------|------|
| Low | tiny `compositing.opacity` shifts, small drifts | ambient loops, idle states |
| Medium | visible but not demanding | most icon and logo beats |
| High | large displacement, demands attention | celebration bursts, hero reveals, stingers |

## Color moves too

Color is a channel, not a coat of paint — a shift in `fill.paint` or `stroke.paint` changes the mood mid-motion. Move *toward* a meaning; don't start already there.

| Color | Feeling | How it should move |
|-------|---------|--------------------|
| Blue | trust, calm | smooth, medium fill transitions |
| Green | success, growth | upward, expansion, gentle overshoot |
| Red | alert, urgency | sharp, fast, horizontal shakes |
| Orange | energy, warmth | bouncy, diagonal paths |
| Purple | premium, mystery | slow reveals, elegant easing |
| Yellow | optimism, caution | quick pulses |
| Teal | modern, clarity | clean, snappy transitions |

**The rules of a color move:**
- Success: transition *to* green — don't open on it, arrive at it.
- Error: flash red, then settle — a sustained red just alarms.
- Warning: pulse yellow/amber so the urgency reads as ongoing.
- Neutral emphasis: use `compositing.opacity`, not a color change — color spends meaning you may not want to spend.

## Default feeling by subject

When the brief doesn't name a feeling, the subject implies one. Start here, then adjust.

| Subject | Default feeling |
|---------|-----------------|
| Checkmark / confirm icon | joy + confidence |
| Warning / alert icon | mild urgency |
| Logo reveal | calm + confidence |
| Directional / arrow motion | confidence |
| Notification badge | mild surprise |
| Loader / spinner | calm |
| Onboarding illustration | curiosity + delight |
| Explainer diagram beat | calm + confidence |
| Purchase / reward burst | joy + confidence |
| Delete / dismiss icon | calm — a respectful departure |
