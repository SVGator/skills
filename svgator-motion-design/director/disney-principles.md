# Disney's 12 Principles — Tuned for SVG

The old hand-drawn laws still hold; they just map onto SVGator channels now. Each one is a way to make motion feel like it obeys physics and has a life of its own.

## 1. Squash and Stretch

Weight reads through deformation — a thing that hits and never squashes feels weightless and fake. Push and preserve volume: as one axis grows, the other shrinks.

- Squash: `transform.scale` ~[1.2, 0.8]; stretch: ~[0.85, 1.15].
- Impact: 2–4 frames (30–65ms). Recovery: 4–8 frames (65–130ms).
- Volume stays constant: x-scale +20% → y-scale drops to match.
- Set `transform.origin` to the contact edge — bottom for a bouncing ball, so it flattens *against* the floor.
- Skip it for premium/elegant logo reveals; deformation reads as cheap there.

## 2. Anticipation

The eye needs a wind-up to believe the payoff — a small move *against* the main direction before the action tells you it's coming.

- Duration 100–200ms, magnitude 10–20% of the main action.
- Icon pop: `scale` down 3% before scaling up. Character leap: crouch (`scale.y` down) first.
- Skip for micro-beats under 150ms — there's no room to wind up.

## 3. Staging

Point the eye at one thing at a time. If everything competes, nothing lands.

- Dim non-hero elements to 40–60% `compositing.opacity`.
- Hero enters 100–200ms *after* its supporting cast, so the stage is set when it arrives.
- One primary action per timing beat.

## 4. Straight Ahead vs. Pose to Pose

Two ways to build a move, each with a feel. Pick by whether you want spontaneity or control.

| Approach | Feel | Best for |
|----------|------|----------|
| Straight ahead | fluid, spontaneous | particle bursts, ambient drift, organic sketch |
| Pose to pose | planned, controlled | icon state changes, logo reveals, morphs |

## 5. Follow-Through and Overlapping Action

Nothing stops all at once — trailing parts keep going after the body settles, and that lag is what makes it feel connected and alive.

- Child parts lag 50–150ms behind the parent.
- Tails, capes, streamers: offset their stop times by 100–200ms.
- Give trailing parts a softer bezier (lower "stiffness") so they overlap more.

## 6. Slow In and Slow Out

Real things ease into and out of motion; only machines move at constant speed. Match the curve to what the move is doing.

| Context | Easing | Why |
|---------|--------|-----|
| Entrance | ease-out | arrives and settles |
| Exit | ease-in | gathers and leaves |
| On-screen move | ease-in-out | a smooth journey both ends |
| Ambient loop | sine ease-in-out | seamless, no visible start/stop |

**Never** linear for spatial movement. Linear belongs only to a continuous `rotate`, a progress fill, or a timer.

## 7. Arcs

Life moves in curves; straight lines read as mechanical. Route `transform.translate` paths through an arc, not a ruler-straight line.

- 10–20px perpendicular offset at the midpoint of the path.
- Subtle (5px) for corporate/utility icons, pronounced (20px+) for mascots and playful marks.
- Straight paths are a *choice* — use them when the subject is genuinely mechanical.

## 8. Secondary Action

The supporting move that makes the primary believable — a shadow answering, a ring expanding. It agrees with the hero without competing.

- Amplitude 30–50% of primary; starts 50–100ms after it.
- Different easing than primary.
- A shape scales in → its cast shadow grows. A checkmark strokes on → a burst ring expands behind it.

## 9. Timing

Duration *is* weight and mood — the same move slow feels heavy, fast feels light. Set it by what the piece should feel like.

| Weight / mood | Duration |
|---------------|----------|
| Heavy (full scenes, big reveals) | 400–800ms |
| Light (icon states, badges) | 100–250ms |
| Sad / serious | 600ms+ |
| Happy / light | 200–400ms |
| Urgent | 100–200ms |

Enter–exit asymmetry: entrances run 30–50% longer than exits — things arrive with care and leave with purpose.

## 10. Exaggeration

Truth reads better than literal. Push past the target and let it settle back; how far is a personality decision.

| Personality | Push |
|-------------|------|
| Playful | 15–25% |
| Energetic | 20–30% |
| Corporate | 0–5% |
| Premium | 0% |

Scale overshoot: 10–30% beyond target (bezier y > 1). Rotation overshoot: ±5–15°.

## 11. Solid Drawing

Keep the form convincing across every keyframe — proportions hold, and light behaves.

- Consistent proportions frame to frame; no accidental warping.
- Combine `transform.scale` + `transform.rotate` to imply depth.
- Cast-shadow behavior tracks the implied light source.

## 12. Appeal

The sum of all of it: motion that's satisfying to watch. Appeal is mostly the absence of the things that break it.

- Smooth curves over sharp angles; timing that feels *right*.
- One personality across every element — one hand, not four.
- Appeal killers: jerky motion, inconsistent timing, abrupt stops, everything animating identically.

## Combining principles

Real pieces stack several at once. These are the reliable recipes.

| Recipe | Principles |
|--------|------------|
| Icon activation | Anticipation + Squash/Stretch + Follow-Through + Secondary + Timing |
| Logo reveal | Anticipation + Arcs + Slow In/Out + Follow-Through + Staging |
| Success burst | Exaggeration + Secondary + Timing + Squash/Stretch + Appeal |
| Error shake | Timing + Slow In/Out + Staging (no exaggeration) |
| Loader loop | Timing + Slow In/Out + Appeal |
