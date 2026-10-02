# Brave Engine — Releases

Downloadable binaries only. No engine source lives in this repository — that stays in the main (private) `brave-engine` repo.

This repo exists for two kinds of releases:

- **NW.js runtime mirrors** — re-hosted copies of [NW.js](https://nwjs.io)'s own official binaries, pinned to the exact version Brave Engine's Build Project packaging depends on (`PACKAGED_NW_VERSION` in `project-builder.ts`). The editor's packaging pipeline (`ProjectBuilder.packageForTarget()`, via [`nw-builder`](https://github.com/nwjs-community/nw-builder)) fetches from here instead of `dl.nwjs.io`/`nwjs.io` directly, so a build never depends on NW.js's own distribution infrastructure staying up or fast. Each release tag is the literal NW.js version it mirrors (e.g. `v0.107.0`) — `nw-builder`'s own URL construction (`{downloadUrl}/v{version}/{file}`) requires that exact shape, not a free choice. Each one also carries `SHASUMS256.txt` (checksums verified against NW.js's own official file before upload) and `versions.json` (the version manifest `nw-builder` otherwise fetches from `nwjs.io`).
- **Editor releases** — packaged Brave Engine editor builds, once those exist.

This repo must stay **public** — GitHub release assets inherit the repository's own visibility, with no per-release override, and both `nw-builder`'s own fetch and an end user's own download need that.
