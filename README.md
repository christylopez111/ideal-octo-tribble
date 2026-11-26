# Détour! updates

This repository is the update server for the Détour! Android app, served by GitHub Pages.

* `ota-manifest.json`: the newest version number and the SHA-256 of every game file.
* `app/`: the game files themselves.

The app reads the manifest, downloads only the files that changed, checks each one against its SHA-256, and switches to the new version the next time it opens. If that version does not start, the app goes back to the version it was installed with.

To publish a new version: build it (`node build.js && node build-apk.js`), copy the contents of `apk/ota-site/` here, and push to `main`.

The app reads these files straight from this repository (raw.githubusercontent.com), so GitHub Pages does not need to be on. Changes reach phones within about five minutes of a push.

## Adding levels

`levels.json` is the list of levels. Each entry is `[game, how hard]`:

* game: `bus`, `metro`, `signs`, `traffic`, `run`, `plow` or `find`
* how hard: a whole number from 1 to 40

Add entries at the end of `route` to add levels (the last entry is the finale). Never remove entries: players keep their stars by level number. The game checks the file and ignores it if anything is wrong, so a typo cannot break the game. Phones pick up the new list the next time the game starts.
