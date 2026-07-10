# Troubleshooting — it animates, but it looks wrong

Craft problems and their fixes. (This skill is about taste, not tooling — if it's exporting static or a channel isn't taking, that's a mechanics issue, not a craft one.)

## It looks wrong

| Symptom | Likely cause | Fix |
|---------|-------------|-----|
| Element swings/orbits when it should scale or spin in place | Pivot (`transform.origin`) is at the corner, not the visual center | Put the origin at the element's visual center before animating scale/rotate. |
| Artwork drifts off-frame once scale/rotate is added | Pivot fighting the element's position | Anchor the pivot at the center it should grow/turn around; give a moving-and-scaling element its own layer so position and pivot don't fight. |
| Looks robotic / mechanical | Linear easing on spatial motion, or straight-line-only paths | Use bezier curves; add an arc via a mid keyframe or a `translate` X-offset. |
| Feels cheap / flat | Only one moving element (primary-only) | Add secondary (shadow, trailing part, offset stroke) + ambient (drift, breathe). ≥2 layers. |
| Motion clips at the edge | Overshoot/float exceeds the canvas | Enlarge the canvas or reduce amplitude; leave headroom for the spring. |
| Loop stutters at the seam | First & last keyframe values differ | Make them identical, or use `alternate` for ping-pong. |
| Morph snaps instead of flowing | Keyframe path node counts differ | Match node counts across morph keyframes (pad the simpler shape). |
| Crossfade/morph shows two states overlapping | Both states are visible mid-swap | Add a brief `blur` filter (~2px) on both during the transition — it blends them into one read. |
| Draw-on doesn't reveal cleanly | `dashArray` shorter than the path, or offset not taken all the way to 0 | Set `dashArray` ≥ path length; animate `dashOffset` from that length → 0. |
| Too slow / sluggish | Duration over the type budget, or ease-in-out where ease-out fits | Trim duration ([timing-easing.md](timing-easing.md)); ease-out reads faster. |
| Too fast / jarring | No easing, or missing settle | Add ease-out minimum; add 50–100ms resolution at the end. |
| No personality | Same generic easing everywhere | Apply one archetype's signature curve + overshoot consistently ([../director/motion-personality.md](../director/motion-personality.md)). |
| Too busy / chaotic (scenes) | Too many elements moving at once | 1/3 rule: ≤1/3 of elements active simultaneously; stagger the rest ([../director/choreography.md](../director/choreography.md)). |
| Reads flat emotionally | No clear emotional target | Pick the feeling first; let it set easing, duration, amplitude ([../director/emotion-mapping.md](../director/emotion-mapping.md)). |

## Quick diagnostic order
1. **Does it read?** Watch it loop / play through — then again in **slow motion** to catch what full speed hides. Is there one clear hero move?
2. **Origins & clipping** — centered pivots, nothing leaving the frame on the spring.
3. **Timing & easing** — right duration for the type, directional easing, seamless seam.
4. **Taste pass** — [quality-checklist.md](quality-checklist.md).
