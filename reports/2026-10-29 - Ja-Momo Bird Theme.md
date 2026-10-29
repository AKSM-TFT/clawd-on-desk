# Ja-Momo Bird Theme

Date: 2026-10-29

Scope: new builtin desktop-pet theme built from the user-supplied animated WebP set
"Klawd on Desk — latest glasses" (`animations/` transparent cutouts, `animations_dark_background/`
charcoal editions, source crops, previews, manifest).

## Change

- Added `themes/ja-momo-bird/`:
  - `theme.json` — schemaVersion 1, name "Ja-Momo Bird", version 1.0.0.
  - `README.md` — asset/pose mapping, measured geometry, validation steps.
  - `assets/` — 10 referenced WebP animations (idle, thinking, typing, coding, error, success,
    surprised, sleep, look-around, drag_3), theme-prefixed basenames, ~1.9 MB total. Drag
    reaction binds only the drag_3 pose (drag_1 / drag_2 removed per user request).

## Behavior

- Before: no Ja-Momo Bird theme existed; the pet rendered only the built-in Clawd / Calico /
  Cloudling themes plus user-importable ones.
- After: the new theme appears in the Settings theme picker (folder discovery is runtime-driven)
  and binds the mascot's full state set: idle (blink + wandering glance), thinking, working
  (typing loop; deeper soldering pose at 3+ live sessions), error, attention (success), notification
  (surprised), sleeping (direct sleep sequence).
- No source-code changes: theme folder + assets only; runtime consumes it through the existing
  theme loader (animated WebP through the `<img>` animation channel). No drag reaction remains.

## Verification

- `node scripts/validate-theme.js themes/ja-momo-bird` — all checks passed (schema, assets,
  hitBoxes, fallback, capabilities).
- `loadTheme("ja-momo-bird", { strict: true })` — ok; `validateThemeShape` ok; discovered as
  builtin; listed via `listThemesWithMetadata()`.
- All 215 tests in the `test/theme-*.test.js` suite pass.
- Repository asset audit — only the pre-existing tracked-tree hard-budget error remains; the new
  theme added ~1.9 MB of WebP assets.

## Issues / Limitations

- Assets could not be visually inspected in this session (image input unavailable); geometry was
  measured numerically from the source PNG previews via a pure-Node PNG decode + alpha bounding-box
  pass, per the raster-theme-geometry workflow.
- Final on-screen placement (pet window framing) still warrants a real desktop smoke run.

## Follow-ups

- Commit the new theme folder (none made yet; GitHub-push rules require branch approval first).
- Optional: user-driven visual tuning of `hitBoxes` / `visibleHeightRatio` on real hardware.

---

# Console Report

```text
Title: Ja-Momo Bird Theme

Changes
1. Added the new "Ja-Momo Bird" animated desktop pet theme with theme.json, README and ten
   WebP animation assets; the drag reaction now binds only the drag_3 pose (drag_1 / drag_2
   removed).
2. Bound idle, thinking, working, error, attention, notification and sleeping mascot states,
   plus coding tier, idle glance animation and direct sleep sequence.

Testing
1. Theme validator passed; loader strict-load and shape validation passed; all 215 theme tests
   passed.

Issues
1. Visual on-screen placement still needs a real desktop smoke run; asset hard-budget finding is
   pre-existing.

Notes
1. Recorded the raster theme geometry workflow verification date — 2026-10-29 — in the project
   knowledge patterns note.

Documentation
1. Change audit: <vault>/clawd-on-desk/changes/<note>.md (not created; small feature edit).
2. Temporary artifacts: None (measure script kept in approved temp dir, not in repo).
```
