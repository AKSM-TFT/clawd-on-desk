GHOST ON DESK
Thinking + Working Animation Pack | Version 1.0.0

INSTALL
-------
Extract the ZIP. Copy the entire ghost-on-desk folder, including theme.json,
into your Clawd user themes directory:

Windows: %APPDATA%\clawd-on-desk\themes\ghost-on-desk\
macOS:   ~/Library/Application Support/clawd-on-desk/themes/ghost-on-desk/
Linux:   ~/.config/clawd-on-desk/themes/ghost-on-desk/

Then open Clawd Settings > Theme and select "Ghost on Desk".
Restart Clawd if the newly copied folder is not listed.

Correct Windows structure:
%APPDATA%\clawd-on-desk\themes\ghost-on-desk\theme.json
%APPDATA%\clawd-on-desk\themes\ghost-on-desk\assets\thinking.apng
%APPDATA%\clawd-on-desk\themes\ghost-on-desk\assets\working.apng

This is a native Clawd theme folder, not a Codex Pet atlas package.
Use the manual folder installation above rather than the Codex Pet ZIP importer.

ANIMATIONS
----------
assets/thinking.apng   Slow head tilt, slight hair sway, animated thought dots.
assets/working.apng    Individually staggered finger taps, head motion, terminal mark.
assets/idle.png        Static pondering pose without the thought bubble.

Both animated files: 384 x 450, 64 frames, 60 ms per frame, 3.84-second loop,
true alpha transparency. There is no audio and no flashing jump scare.

extras/gif/           GIF versions with binary transparency.
extras/source/        Clean source poses for further editing.
preview.html          Open locally in a browser to view both animations.
CHECKS.json           File-integrity and animation validation results.

STATE COVERAGE
--------------
Thinking and working are the two bespoke animated states requested.
Idle, sleeping, waking, error, attention, and notification use idle.png.
Sweeping, carrying, and juggling reuse the working animation.
These are intentional fallbacks, not additional unique animations.
Eye tracking, mini mode, accessories, and click reactions are not included.

USE ONLY THE TWO ANIMATIONS IN AN EXISTING THEME
----------------------------------------------
Copy thinking.apng and working.apng into that theme's assets folder.
Merge these two entries into its existing states object in theme.json:

  "thinking": ["thinking.apng"],
  "working": ["working.apng"]

Do not replace the rest of that theme.json. Existing workingTiers entries
may override the base working asset; change those deliberately if needed.
This pack is designed around a shared 128 x 150 logical canvas. A different
theme's canvas, layout, or hitboxes may need alignment adjustments.

TESTING
-------
All 128 APNG frames were decoded and matched against the rendered frames.
Both GIFs were checked for frame count and transparent backgrounds. The
manifest was parsed and its asset references and shared dimensions checked.
Not run inside the Clawd Electron app; the official validator was not run here.
For an additional check from a Clawd source checkout, run:

  node scripts/validate-theme.js path/to/ghost-on-desk

Artwork was generated from the image supplied in this conversation and then
animated. This package does not assert ownership of the original reference.
No bundled Clawd character artwork or application source code is included.

FORMAT / INSTALLATION REFERENCES
-------------------------------
https://github.com/rullerzhou-afk/clawd-on-desk
https://github.com/rullerzhou-afk/clawd-on-desk/blob/main/docs/guides/guide-theme-creation.md
Documentation checked September 28, 2026.
