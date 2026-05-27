# RadResults Releases

Public release channel for the RadResults Electron desktop app. This repo
contains **no source code** — only published installers (`.exe`, `.dmg`,
`.zip`) and their accompanying `latest*.yml` + `*.blockmap` files that
electron-updater needs at runtime.

The source code lives in the private
[thultgren/Rad-Results](https://github.com/thultgren/Rad-Results) repo and
is mirrored here as release artifacts on every tag.

## Why a separate repo?

`thultgren/Rad-Results` is private, so its releases can't be fetched
without authentication. electron-updater on an installed user's machine
needs to fetch `latest.yml` over plain HTTPS without credentials. Publishing
to a public mirror is the standard pattern for this case.

## Channels

Releases use prerelease versions (e.g. `v0.1.0-test.1`) routed to the
electron-updater `test` channel until the v1.0.0 stable release. The
channel routing is configured in:

- `package.json` → `build.publish` (source repo) — tells electron-builder
  WHERE to upload.
- `src/main/updater.ts` → `autoUpdater.channel = 'test'` (source repo) —
  tells the installed app WHICH releases to consider.

## Adding a release

Tag a commit in `thultgren/Rad-Results` matching `v*` and push the tag.
The `Release builds` workflow there publishes here automatically.
