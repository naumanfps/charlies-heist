# Charlie's Heist — Unity WebGL build output

This directory receives the Unity WebGL export for **Charlie's Heist**. No
binaries are committed yet; the game content record
(`src/content/games/charlies-heist.json`) ships with `enabled: false` until a
real build lands here.

The `../runtime.html` launcher loads exactly these four files from this
directory (the Unity project's output product name must be `charlies-heist`):

- `charlies-heist.loader.js`
- `charlies-heist.framework.js`
- `charlies-heist.wasm`
- `charlies-heist.data`

Export checklist (matches the site's launcher contract):

1. Platform: WebGL, Product name `charlies-heist`, Company `Inari Games LLC`.
2. Copy the four files above into this `Build/` folder (keep the names —
   `runtime.html` builds its URLs from `buildUrl = "Build"` + `charlies-heist.*`).
3. Copy the Unity `TemplateData/` folder next to `runtime.html` (favicon + style).
4. Daily puzzle data is NOT shipped here — see
   `../StreamingAssets/CharliesHeist/README.md`.
5. When the build is live and tested, flip `status` to `"published"` and
   `enabled` to `true` in the content record so `tests/site-integrity.test.js`
   starts enforcing these artifacts.
