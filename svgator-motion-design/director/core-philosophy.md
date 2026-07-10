# Core Philosophy

Motion that reads as *designed* rests on three things: it feels like something before it means anything, it tells a tiny story even in 200ms, and it never moves on one layer alone. Get those right and the piece has a hand behind it. Miss them and it reads as a tween.

## Feeling comes before the channel

Name the emotion first. The feeling picks the easing, the pace, and the amplitude — the channel is just how you deliver it. Pick the channel first and you end up decorating a mood you never chose.

| Emotion | How it moves | Beats run | Easing |
|---------|--------------|-----------|--------|
| Trust | smooth, predictable, nothing sudden | 300–400ms | gentle curves |
| Delight | bouncy, a little surprising | 200–300ms | overshoot (bezier y past 1) |
| Urgency | sharp, direct, no wind-up | 100–200ms | snappy ease-out |
| Calm | slow, flowing, never in a hurry | 500–1000ms | sine ease-in-out |
| Surprise | sudden, explosive | 150–300ms | ease-out-expo |
| Confidence | direct, decisive, lands square | 200–400ms | strong ease-out |

## Even a fade has three acts

Every piece, however short, wants a setup, an action, and a resolution — because the eye needs to be prepared, shown, and let go. A 200ms icon fade still has all three, compressed. Skip the resolution and it stops mid-breath; skip the setup and it feels like it started without you.

| Phase | Share of the runtime | What it's doing |
|-------|----------------------|-----------------|
| Setup | 20–30% | establish context, ready the eye |
| Action | 30–40% | the hero move, the thing it's actually about |
| Resolution | 30–40% | settle, breathe, confirm it landed |

## The craft that separates it from a tween

- Easing carries the emotion — a spatial move without a felt curve is dead on arrival.
- Duration scales with size and travel: a big shape crossing far takes longer than a small one nudging.
- Arcs for anything organic, straight lines only for the mechanical.
- Secondary motion sells belief: a cast shadow reacting, a stroke trailing, a related shape answering.
- Nothing starts and stops all at once — that hard sync is the machine showing through.

## Three layers, always

One element sliding in is what every default does. Motion that looks authored runs on three layers at once, and the lag between them is what sells it.

| Layer | What it is | Amplitude |
|-------|------------|-----------|
| Primary | the one move the eye follows | 100% |
| Secondary | the supporting cast that makes it believable | 30–50% |
| Ambient | the life underneath, never asking for attention | 10–20% |

Secondary arrives 50–100ms *behind* primary on a different curve — that offset is the whole trick. Ambient is slow and continuous and never demands a look. A logo mark scales in (primary), its wordmark strokes draw on via `stroke.dashOffset` (secondary), a soft glow breathes under it (ambient). Ship primary alone and it reads cheap — that's the single most common tell.

## The 1/3 canvas rule

Nothing travels more than a third of the viewBox without a keyframe changing its direction, speed, or arc — because the eye disbelieves a shape that crosses a long distance at constant velocity in a straight line. Break the run with a curved `transform.translate` path instead of a flat one, or a shift in pace.

## The attention budget

The eye can follow one hero at a time; give it two and it picks one and misses the other.

- One hero move per beat.
- Two, at most three, elements in active motion at once.
- Ambient (a loop glow, a slow drift) doesn't count against the budget — it's below the threshold of notice.
- Stagger instead of synchronizing; a synchronized crowd reads as a single flat object.
