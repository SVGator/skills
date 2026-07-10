# Quality Checklist — the motion-designer approval gate

Run before delivery. Severity tiers first (fix CRITICAL always), then the full pass.

## CRITICAL — a "no" here means it's broken
- [ ] No linear easing on spatial/scale motion (linear only for continuous spin/progress)
- [ ] Transform origins set to visual centers — nothing pivots from the corner unintentionally
- [ ] Nothing clips at the canvas edge on overshoot/float
- [ ] At least a primary motion layer exists and reads clearly
- [ ] Loops are seamless at the seam (first/last keyframe match) or intentionally `alternate`

## HIGH — a "no" here means it looks amateur
- [ ] ≥2 motion layers (primary + secondary and/or ambient) — not one lonely shape
- [ ] Duration fits the animation type — not sluggish, not frantic (see [timing-easing.md](timing-easing.md))
- [ ] Directional easing correct: ease-out entrances, ease-in exits, sine ambient loops
- [ ] One consistent personality — signature curve + overshoot applied throughout ([../director/motion-personality.md](../director/motion-personality.md))
- [ ] Secondary motion trails the primary (50–150ms offset, different easing)
- [ ] Setup → action → resolution present; ends on a resolved pose (one-shot) or breathes before repeating (loop)

## MEDIUM — a "no" here means it could be better
- [ ] Emotion identified and legible in the motion ([../director/emotion-mapping.md](../director/emotion-mapping.md))
- [ ] Arcs, not dead-straight paths, where organic motion is wanted
- [ ] Anticipation on large/important moves (small counter-move before the action)
- [ ] Overshoot budget matches personality (Premium 0 → Energetic ~1.5)
- [ ] Scenes: 1/3 rule respected (≤1/3 elements moving at once), staggered, one hero
- [ ] Counter-motion / follow-through where it adds life

## The taste questions (ask them out loud)
- **Does it read on the 100th loop?** (loops) / **Does it land?** (one-shots)
- **Is there a hero?** One clear thing the eye follows, not everything competing.
- **Would I ship this?** If it feels like a default tween, it isn't done — apply personality, layer it, add the settle.
- **Is the motion the minimum that carries the idea?** Two channels beats five. One clear idea per icon.
- **Would someone believe an AI made this?** If a default-tween look is even plausible, it isn't done. You want people asking *how did they make this*, not *which tool generated this*.

## Review it the way a motion designer does
- **Watch it in slow motion** — 2–5× longer, or scrub the timeline. Stalls, easing that hitches, and origins that swing are invisible at full speed.
- **Step the seams frame by frame** — the loop repeat, a morph, a crossfade — where two states can overlap wrong.
- **Come back the next day.** Fresh eyes catch the stutter you stopped seeing. If it still reads clean cold, it's done.

If it clears CRITICAL + HIGH and you'd genuinely ship it, it's done. If anything looks wrong, diagnose it in [troubleshooting.md](troubleshooting.md).
