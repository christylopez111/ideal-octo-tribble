# Détour! updates

This repository is the update server for the Détour! Android app, served by GitHub Pages.

* `ota-manifest.json`: the newest version number and the SHA-256 of every game file.
* `app/`: the game files themselves.

The app reads the manifest, downloads only the files that changed, checks each one against its SHA-256, and switches to the new version the next time it opens. If that version does not start, the app goes back to the version it was installed with.

To publish a new version: build it (`node build.js && node build-apk.js`), copy the contents of `apk/ota-site/` here, and push to `main`.
