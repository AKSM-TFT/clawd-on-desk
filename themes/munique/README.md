# Munique

Black-and-white tuxedo cat desk mascot. Every state is a two-frame APNG loop built from the
`clawd_chibi_cat_assets` sticker pack, so the cat shifts pose instead of freezing on one
frame.

## Assets

| File | Frames | Source poses (`clawd_chibi_cat_assets`) |
|------|--------|------------------------------------------|
| `assets/idle.apng` | sitting ↔ licking paw | `idle/cute_tuxedo_cat_sticker.png`, `idle/chibi_tuxedo_cat_grooming_paw.png` |
| `assets/thinking.apng` | hugging yarn ball ↔ rolling with it | `thinking/chubby_cat_hugging_red_yarn.png`, `thinking/playful_cat_hugging_red_yarn.png` |
| `assets/working.apng` | kneading dough | `coding/cute_cat_kneading_dough_sticker.png`, `coding/kawaii_cat_kneading_dough_sticker.png` |

`juggling` reuses `working.apng`, and `sleeping` falls back to `idle`.

## Geometry

- Source keyframes are 1254 x 1254 transparent PNGs; the shipped APNGs are exact 2x box
  downscales at 627 x 627, keeping the 512 viewBox 1:1 with the art.
- Each pair was translated before downscaling so its alpha box sits on the same feet line
  (`y = 1194` in source space, `y = 597` after downscaling). Without that, poses with
  different canvas margins bob between frames and between states.
- `layout.contentBox` stays canvas-sized and `visibleHeightRatio` stays at 0.62, the value
  tuned for this card style; `fileHitBoxes` are measured from the per-file alpha union and
  centred on the viewBox axis.

## Provenance

The source pack (`idle/`, `thinking/`, `coding/`, `extras/`) is not kept in the repository
because `themes/**` ships inside the packaged app. Only the frames bound above are
materialized here. The unused poses (`playful_tuxedo_cat_with_red_yarn.png`,
`kawaii_cat_kneading_dough.png`, `extras/cute_chibi_black_and_white_cat_sticker.png`) are
kept out on purpose.
