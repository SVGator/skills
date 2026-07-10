# What Each Channel Says

Every channel in SVGator carries a connotation before it carries any motion. The craft is choosing the one that *means* what you're saying — not just the one that happens to move. Here's what each one says, and how to pair them.

## `transform.translate` — where a thing goes

Direction is meaning. A shape that rises reads as growth; the same shape sinking reads as settling. Move it the way the story runs.

| Direction | What it says |
|-----------|--------------|
| Upward | growth, improvement, aspiration |
| Downward | settling, completion, grounding |
| Leftward | regression, backward, departure |
| Rightward | progression, forward, arrival |
| Toward center | focus, convergence |
| Away from center | distribution, expansion |

## `transform.scale` — how much it matters

Scale is the fastest way to say *this is important* — but a pop that never settles reads as a glitch, not emphasis. Let it overshoot and come back.

| Move | What it says |
|------|--------------|
| Scale up | importance, activation, proximity |
| Scale down | deprioritization, distance |
| Pulse | attention, heartbeat, life |
| Breathing | presence, waiting (loops) |

Set `transform.origin` deliberately: the visual center for a clean pop, an edge for a hinge or an anchored grow. Get the origin wrong and the shape swings from its corner.

## `transform.rotate` — turning as meaning

How far something turns changes what the turn *is* — a nudge is an adjustment, a full revolution is a process running.

| Amount | What it says |
|--------|--------------|
| Small (5–15°) | subtle adjustment, wobble |
| Medium (45–90°) | transformation |
| Full (360°) | completion, processing |
| Continuous | ongoing activity (spinners) |

## `compositing.opacity` / `fill.opacity` — presence and absence

Fading is arrival and departure — but a fade alone has no body to it. It's the thinnest channel; never let it carry a moment by itself.

| Move | What it says |
|------|--------------|
| Fade in | arrival, materialization |
| Fade out | departure, dissolution |
| Partial | secondary, ghosted, background |

**The rule:** never opacity alone for a moment that matters. Pair it with a `translate` or a `scale` so the thing has weight as it appears.

## `stroke.dashOffset` (+ `dashArray`) — a line drawing itself

Nothing else says *being made by hand* like a stroke drawing on. It's the whole reason line art feels alive instead of pasted.

| Technique | What it says |
|-----------|--------------|
| dashOffset draw-on | handwriting, sketching, building, self-assembly |
| dashOffset erase-off | undoing, unwriting, dissolving a line |
| `stroke.width` pulse | emphasis, energy running along a contour |

The go-to for signatures, outlined icons, logo strokes, and connector paths.

## `shape.path` — one thing becoming another

Morphing is transformation you can watch happen — no cut, no swap, a continuous becoming.

| Technique | What it says |
|-----------|--------------|
| Morph between node arrays | transformation, one-thing-becomes-another |

Keep node counts matched or the morph tears. Reach for it on icon-to-icon state changes, liquid blobs, expression changes.

## `fill.paint` / `stroke.paint` — color as state

Color shifts read as a change in *state* — going, stopping, waking up, spending out. Move toward the meaning; don't open on it.

| Transition | What it says |
|------------|--------------|
| To green | success, go |
| To red | error, stop |
| To blue | trust, active |
| To gray | inactive, spent |
| Brightening | activation, focus |
| Dimming | deactivation, recede |

## Pairing channels

Two channels is the sweet spot — one reads thin, three reads busy. The primary carries the meaning; the second is polish.

| Combination | Best for |
|-------------|----------|
| translate + opacity | elements appearing / disappearing |
| scale + opacity | marks, badges, pop-ins |
| translate + scale | hero focus, emphasis |
| rotate + scale | celebrations, playful activation |
| translate + rotate | organic, tumbling motion |
| color + scale | state emphasis |
| dashOffset + fill.opacity | draw the outline, then fill it |

## Channels by goal

The reliable primary/secondary for each common job — and the channel to *avoid*, because it fights the read.

| Goal | Primary | Secondary | Avoid |
|------|---------|-----------|-------|
| Entrance | translate | opacity | rotation |
| Exit | translate | opacity | scale up |
| Icon activation | scale | color | translate |
| Success burst | scale | color + opacity | translate |
| Alert / error | translate (shake) | color | scale |
| Loader loop | rotation | opacity | translate |
| Line-art reveal | stroke.dashOffset | opacity | scale |
| Icon-to-icon morph | shape.path | color | rotation |
| Badge / notification | translate + scale | opacity | rotation |
| Dismiss / delete | scale + opacity | translate | grow |
| Selection / highlight | scale | color, opacity | rotation |
| Progress fill | translate or scale | color | opacity |

## Easing lives on the keyframe

The channel says *what*; the easing says *how it feels* — and in SVGator each keyframe carries its own curve. A bezier's y is unbounded, so pushing it past 1 springs the shape into place with no extra keyframe. Keep linear for a continuous `rotate` or a progress fill; give every spatial arrival a bezier ease-out; use steps for a stop-motion or tick effect. → [timing-easing.md](timing-easing.md)
