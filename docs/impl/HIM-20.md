# HIM-20 — show best technical projects on README

## Summary

The current profile README is heavily themed but its "Selected missions" are not the strongest
engineering work. Four of the six featured cards are a community site (SFC-foundations), a CRUD
medical-records app (parchiapp), a VS Code colour theme (GTA-VC), and a Reddit meme bot (MEMEBOT).
The two genuinely technical cards (passit and sketchetc) are buried among them, while newer,
substantially harder projects (auricle, contractwatch, yaadon-ki-rasoi, Vyral) are not shown at all.

This ticket re-audits every public, non-fork repo owned by `himanshu007-creator`, ranks them by
engineering depth and public verifiability, and proposes a new six-card selection plus a demoted
vault. SFC-foundations is removed from the README entirely rather than demoted (decided). Every
recommended link was checked as publicly reachable on 2026-10-22 (GitHub repos and live demos
return `200`; npm, PyPI, crates.io and Hugging Face package metadata resolve).

No prior HIM-20 work was found: `docs/impl/` did not exist and there is no stray branch, doc or
partial README edit beyond the current redesign commit (`33b6862`).

Audit verdict on the current README list:

| Current entry | Real engineering? | Verdict |
|---|---|---|
| passit | Yes — Rust MCP server, SQLite, published crate, CI | Keep, promote as a proof point |
| sketchetc | Yes — 100 commits, Swift/Shell macOS system, releases, CI | Keep |
| SFC-foundations | No — community/static site, popularity not engineering | Remove from README |
| parchiapp | Moderate — full-stack Next.js/Express/MongoDB CRUD | Demote to vault |
| GTA-VC | No — VS Code colour theme | Demote to vault |
| MEMEBOT | No — small Reddit bot | Demote to vault |

Recommended new featured set: **auricle, passit, contractwatch, yaadon-ki-rasoi, Vyral,
sketchetc**. Recommended vault: **Multi-Modal-Evidence-Review, parchiapp, OMRZen, GTA-VC,
MEMEBOT**. Do not link SFC-foundations anywhere in the README.

## Files involved

- `README.md`
  - lines 38–86: "🎮 Selected missions" six-card table — replace four cards, reorder all six.
  - lines 88–99: "🗂️ More from the vault" table — add Multi-Modal-Evidence-Review, keep the
    demoted projects, remove SFC-foundations, and correct the implied ranking.
  - lines 103–115: "🧰 Loadout" — optional only; no change required for this ticket.
- `docs/impl/HIM-20.md` — this research/implementation note.
- No build files, assets, GIFs or badges need to change. The README is pure Markdown + hosted SVGs
  and has no build step or test harness.

## Approach

### 1. Replace the four weak mission cards

Keep the existing two-column `<table>` layout, heading, emoji style and Vice City palette. Each
card should keep at most one star badge and one or two stack badges so the table stays readable on
mobile.

**auricle** — highest engineering depth; replaces SFC-foundations.
- Link: https://github.com/himanshu007-creator/auricle
- Proof links: https://www.npmjs.com/package/auricle, https://www.npmjs.com/package/auricle-react,
  https://huggingface.co/auricle-voice/auricle-v1,
  https://himanshu007-creator.github.io/auricle/
- Copy: "Real-time voice activity detection, turn-taking and barge-in for browser voice agents. A
  Rust audio engine compiled to WebAssembly, an in-house model, and drop-in `vad-web`
  compatibility. Published as `auricle` + `auricle-react`."
- Badges: npm `auricle`, Rust, WebAssembly, live demo, Hugging Face model.
- Evidence: `crates/auricle-{dsp,vad,turn,text,worklet,brain,eval}`, `bench/` with latency,
  accuracy and browser-matrix harnesses, `docs/COMPARISON.md`, CI + Pages + release workflows,
  `v0.1.1` release.

**passit** — keep, move to a top slot.
- Link: https://github.com/himanshu007-creator/passit
- Proof links: https://crates.io/crates/passit,
  https://github.com/himanshu007-creator/passit/pkgs/container/passit
- Copy: existing copy is accurate; add "published on crates.io" and keep Docker/MCP tags.
- Evidence: 21 commits, Rust 2024, `rmcp`, SQLite, history importers for Claude/Gemini/OpenCode,
  tool integration tests, CI + Docker + release workflows, crate `1.0.5` with 119 downloads.

**contractwatch** — replaces parchiapp.
- Link: https://github.com/himanshu007-creator/contractwatch
- Proof links: https://pypi.org/project/contractwatch/,
  https://himanshu007-creator.github.io/contractwatch/
- Copy: "Catches breaking FastAPI changes before clients do. Diffs OpenAPI contracts, flags schema
  collisions and async/timeout pitfalls, then blocks the commit or CI run. Python, on PyPI."
- Badges: PyPI, Python, CI, live docs site.
- Evidence: 18 test modules, `compare.py`, `collisions.py`, `reliability.py`, baseline cache and
  reporting layers, GitHub Actions CI, PyPI `1.0.0`.

**yaadon-ki-rasoi** — replaces GTA-VC.
- Link: https://github.com/himanshu007-creator/yaadon-ki-rasoi
- Proof link: https://yaadon-ki-rasoi.vercel.app
- Copy: "Find a childhood dish from a description, not its name. A Next.js pipeline over SerpApi
  search, Trends, YouTube transcripts and Maps, streamed over SSE, with on-device Chrome AI and
  share-card/PDF export."
- Badges: Next.js, TypeScript, live demo.
- Evidence: Next.js 15 / React 19, `lib/agent/*` pipeline, `lib/serp.ts` cache + replay + budget,
  streaming API routes, Vitest, IndexedDB history, Vercel deployment.

**Vyral** — replaces MEMEBOT.
- Link: https://github.com/himanshu007-creator/Vyral
- Proof link: https://vyral-ivory.vercel.app
- Copy: "A playable GTA VI-style in-game phone built around the Unlayer React Image Editor: four
  reskinned editors, canvas video burn-in via MediaRecorder, IndexedDB persistence and URL-as-state."
- Badges: React, JavaScript, live demo.
- Evidence: React 19/Vite, four app-specific editor skins, `src/lib/video.js` frame burn-in,
  `src/lib/clout.js` progression, IndexedDB, 4 commits but a large, working surface.

**sketchetc** — keep.
- Link: https://github.com/himanshu007-creator/sketchetc
- Proof link: https://himanshu007-creator.github.io/sketchetc/
- Copy: existing copy is accurate; trim to one sentence and keep the release/star badge.
- Evidence: 100 commits, 15 stars, active `develop` branch, 7 CI/security workflows, `v1.4.1`
  release, Swift and Shell widgets, installer with upgrade path.

### 2. Rebuild the vault as an honest secondary tier

Replace the four-row vault with five rows, newest/most technical first:

| Project | What | Why it is here |
|---|---|---|
| [Multi-Modal-Evidence-Review](https://github.com/himanshu007-creator/Multi-Modal-Evidence-Review) | Multi-agent VLM claim-evidence reviewer | HackerRank Orchestrate submission; 98 test files, evaluation harness, 22 commits |
| [parchiapp](https://github.com/himanshu007-creator/parchiapp) | Medical records PWA | Full-stack Next.js + Express + MongoDB, live demo; CRUD rather than novel engineering |
| [OMRZen](https://github.com/himanshu007-creator/OMRZen) | Browser OMR sheet checker | Next.js, live demo; small but complete product |
| [GTA-VC](https://github.com/himanshu007-creator/GTA-VC) | Vice City VS Code theme | 7 stars; personality, not engineering |
| [MEMEBOT](https://github.com/himanshu007-creator/MEMEBOT) | Reddit meme bot | 5 stars; fun, small surface |

SFC-foundations is removed from the README entirely, not moved to the vault. Its contributor story
is already covered by the "Rap sheet" Hacktoberfest/GSSoC line, so no replacement copy is needed.

### 3. Link and copy rules

- Include only links verified public: GitHub repos, live demos, npm/PyPI/crates.io/HF package
  pages. Do not link to local previews, forks, or private dashboards.
- Do not repeat unverified superlatives from project READMEs (for example Auricle's benchmark
  table or Vyral's "no backend" claim). Describe what the repo actually contains.
- Preserve the existing badge style: `badgen.net/github/stars/...` for stars, `img.shields.io` for
  stack and package badges, `labelColor=1b0d33` and the `ff6ec7`/`9b5de5`/`0bd3d3` palette.
- Keep `alt` text on every image and `target`-free plain links, matching the file's current style.
- Set the Vyral repo name with its real casing in the URL path (`Vyral`); GitHub is
  case-insensitive but the canonical path is uppercase.
- Leave `hdr.gif`, `ftr.gif`, `MSG.gif`, `secret.png`, badges and the STL untouched.

## Risks

- **Popularity drop is visible.** SFC-foundations has 237 stars; the new technical cards have
  0–15. The README may look less impressive to a star-counting reader. Mitigation: show package,
  demo and test proof (npm/PyPI/crates/HF/CI) instead of leaning on stars.
- **Very recent projects.** auricle (7 commits, created 2026-10-18) and contractwatch (3 commits,
  created 2026-10-13) are new and could read as weekend work. Their crates/npm/PyPI releases,
  tests and demos are the counter-evidence; do not inflate the commit history.
- **Link rot / bot blocking.** GitHub, PyPI, Hugging Face and all demos returned `200`; the npm
  web UI and crates.io web UI returned `403`/`404` to `curl` while their registry APIs returned the
  packages. Re-check links in a browser before merging.
- **Badge dependency.** `badgen.net` and `img.shields.io` can rate-limit or fail; a broken badge
  leaves a broken image. Prefer one star badge per card and keep the package badges simple.
- **Unverified claims.** Auricle's benchmark numbers and Vyral's integration details come from the
  project READMEs, not from this audit. The profile copy should describe architecture, not repeat
  performance claims that were not re-run.
- **Licensing nuance.** Vyral is public but has no license; do not label it open source. sketchetc
  uses CC BY-NC-ND 4.0; passit, auricle and contractwatch are MIT.
- **Mobile table width.** The two-column HTML table is already tight on narrow screens; adding
  long descriptions or many badges makes it worse. Keep descriptions to two short sentences.
- **Removing SFC removes the strongest social proof.** The 237-star / 124-fork project is gone
  entirely, not just demoted. Accepted: the "Rap sheet" still carries the Hacktoberfest/GSSoC
  contributor story, so do not re-add SFC without a new decision.
- **Ordering is a judgment call.** "Most technical" is not a single metric; the proposed order
  weights systems depth, public proof and recency, not stars.

## Tests

This repo has no build, lint or test command. Verification is manual plus link checks.

1. Render `README.md` in GitHub's preview at desktop and mobile widths; confirm the 2×3 table does
   not overflow and all six cards align.
2. Check every `href` and `src` in the changed sections:
   - `curl -s -o /dev/null -w '%{http_code}' -L <url>` for GitHub repos and demos (expect `200`).
   - npm: `curl -s https://registry.npmjs.org/auricle` and `.../auricle-react` (expect `0.1.1`).
   - PyPI: `curl -s https://pypi.org/pypi/contractwatch/json` (expect `1.0.0`).
   - crates.io: `curl -s -H 'User-Agent: ...' https://crates.io/api/v1/crates/passit` (expect
     `1.0.5`).
   - Hugging Face: `curl -s -o /dev/null -w '%{http_code}' https://huggingface.co/auricle-voice/auricle-v1`
     (expect `200`).
3. Confirm badgen/shields URLs return SVG (`curl -sI <badge-url> | grep -i content-type`).
4. Check dark and light GitHub themes; the neon palette must remain readable.
5. `git diff --check` for whitespace, then read the rendered diff to confirm no file outside
   `README.md` changed.
6. Confirm every linked repo is public and non-fork:
   `gh repo view himanshu007-creator/<repo> --json visibility,isFork`.

## Open questions

None. Resolved: remove SFC-foundations from the README entirely (not demote it to the vault).
