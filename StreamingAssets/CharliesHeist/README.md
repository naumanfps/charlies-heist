# Charlie's Heist — StreamingAssets

This folder holds the **single local-development sample fixture** only:

- `puzzles.json` — `{ "puzzles": [ <complete Charlie's Heist sample puzzle> ] }`,
  wrapped verbatim from `Charlies_Heist_Sample_Puzzle.json` in the developer
  package. It is the dev fallback pool the server reads when `POOL_DIR` is not
  configured (see `src/lib/schedule/resolver.ts`), which is exactly what lets
  the game be developed and tested with no running backend.

**Never put the real daily pool here.** Anything inside `public/` is
downloadable by anyone, and the puzzle JSON contains the full answer keys
(correct routes, trivia answers, both 58-node graphs). The production pool
lives in a private `POOL_DIR`; each UTC day the server serves exactly ONE
complete puzzle document through `GET /api/daily/charlies-heist/` and past
days only through the gated archive endpoints. When the private pool is
bootstrapped (`npm run schedule:bootstrap`), this public copy should be
reduced to the dev fixture or removed per the launch checklist.

The Unity project expects this path as its `streamingAssetsUrl` base
(`StreamingAssets/CharliesHeist/...` relative to `runtime.html`).
