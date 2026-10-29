# Ja-Momo Bird

Animated desk mascot built from the "Latest Glasses" animated WebP set: the glasses girl,
the laptop and the glowing electronics box all stay in frame while the poses loop.

## Assets

| File | Source animation | Used for |
|------|------------------|----------|
| `assets/ja-momo-bird-idle.webp` | `animations/idle.webp` | `states.idle` (direct stare and blink loop) |
| `assets/ja-momo-bird-thinking.webp` | `animations/thinking.webp` | `states.thinking` (thoughtful pose and question mark) |
| `assets/ja-momo-bird-typing.webp` | `animations/typing.webp` | `states.working` (keyboard activity) |
| `assets/ja-momo-bird-coding.webp` | `animations/coding.webp` | `workingTiers` (3+ live sessions -> soldering the glowing box) |
| `assets/ja-momo-bird-error.webp` | `animations/error.webp` | `states.error` (shadow face, glowing red eyes, rising hair) |
| `assets/ja-momo-bird-success.webp` | `animations/success.webp` | `states.attention` (sparkles and celebratory LEDs) |
| `assets/ja-momo-bird-surprised.webp` | `animations/surprised.webp` | `states.notification` (shock and motion marks) |
| `assets/ja-momo-bird-sleep.webp` | `animations/sleep.webp` | `states.sleeping` (breathing and floating Zs) |
| `assets/ja-momo-bird-look-around.webp` | `animations/look_around.webp` | `idleAnimations` (wandering glance) |
| `assets/ja-momo-bird-drag_3.webp` | `animations/drag_3.webp` | `reactions.drag` (Dragging pose 3: full reach; drag_1 / drag_2 removed) |

All animations are 640 x 640 WebPs, 16 frames at 12 fps, looping. The transparent-cutout set
(`animations/`) is what ships with the theme; the charcoal-background editions in
`animations_dark_background/` stay out of the pet render channel and are only kept for
reference/desk-background use.

## State mapping

- `idle` -> blinking stare loop; `idleAnimations` -> wondering glance pool
- `thinking` -> thoughtful pose with question mark
- `working` -> typing loop; `workingTiers[minSessions=3]` -> deeper soldering pose with the
  glowing electronics box
- `error` -> shadow face with glowing red eyes
- `attention` -> success pose with sparkles and celebratory LEDs
- `notification` -> surprised pose with motion marks
- `sleeping` -> gentle breathing loop with floating Zs; `sleepSequence.mode` is `direct`
- No drag reaction for drag_1 / drag_2; the drag reaction now binds only the drag_3 pose
  (`ja-momo-bird-drag_3.webp`) — dragging plays just the drag_3 (full reach) pose.

No mini mode, no eye tracking, no head/mouth accessories (the art carries its own expressions).

## Geometry (measured from the source previews)

- `viewBox`: `{ x: 0, y: 0, width: 640, height: 640 }` (source canvas)
- `layout.contentBox`: union alpha box of the shipped poses, `{ x: 30, y: 103, width: 580, height: 482 }`
- `layout.centerX` / `layout.baselineY`: content centre `320` and the shared feet line `585`
- `layout.visibleHeightRatio`: `0.92` (character fills the content box)
- `layout.baselineBottomRatio`: `0.05`
- `hitBoxes.default` plus per-file `fileHitBoxes` for every shipped pose, measured from the
  same alpha boxes (idle `{ x: 30, y: 139, w: 580, h: 446 }`, thinking `{ x: 30, y: 115, w: 580, h: 470 }`,
  typing `{ x: 30, y: 152, w: 580, h: 433 }`, coding `{ x: 30, y: 190, w: 580, h: 395 }`,
  error `{ x: 30, y: 103, w: 580, h: 482 }`, success `{ x: 30, y: 114, w: 580, h: 471 }`,
  surprised `{ x: 30, y: 120, w: 580, h: 465 }`, sleep `{ x: 30, y: 148, w: 580, h: 437 }`,
  look-around `{ x: 30, y: 123, w: 580, h: 462 }`)
  so per-pose hitboxes resolve instead of silently falling through to empty space.

## Validation

```bash
node scripts/validate-theme.js themes/ja-momo-bird
```
