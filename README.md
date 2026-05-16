# QPin Firmware

This repository hosts the Over-The-Air (OTA) firmware updates and the landing page for QPin. It serves firmware binaries directly to the QPin iOS App, enabling seamless, wireless updates for QPin badges.

## Overview

- **Firmware Binary**: The compiled firmware (`.bin`) files are stored in the `firmware/` directory.
- **OTA Portal**: `index.html` provides a mobile-optimized web page with update instructions, release notes, and manual download links.
- **Manifest**: `manifest.json` tracks the latest firmware version, download URL, and minimum battery requirements for the iOS app to verify before initiating an update.

## Releasing a New Firmware Version

1. **Compile**: Export the latest firmware as a compiled binary (e.g., `QPin_vX.X.ino.bin`).
2. **Upload**: Place the `.bin` file inside the `firmware/` folder.
3. **Update Manifest**: Edit `manifest.json` with the new version details:
   - `version` / `build`: Version string and build integer.
   - `releaseDate`: Release date (YYYY-MM-DD).
   - `fileName`: The exact name of the binary.
   - `url`: The absolute URL to the new binary.
   - `notes`: Brief summary of changes.
4. **Update Portal**: Edit `index.html` to reflect the new version number, release date, and detailed release notes.
5. **Deploy**: Commit and push changes. The updates will be served via GitHub Pages.

## OTA Update Process

When users check for updates in the QPin iOS app, the app fetches `manifest.json`, compares the `versionCode`, and ensures the badge has at least a 50% charge. It then downloads the `.bin` file and streams it to the badge over Bluetooth Low Energy (BLE).
