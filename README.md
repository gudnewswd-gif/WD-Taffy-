# WD😘Taffy V7 — website + Android wrapper

## What is included
- `www/index.html`: WD😘Taffy V7.
- `www/manifest.webmanifest`, `www/sw.js`, and icons: basic installable PWA shell and static asset cache.
- `package.json`, `capacitor.config.json`: starting point for a Capacitor Android wrapper.

## Deploy the website with GitHub Pages
1. Open your repository and replace its `index.html` with `www/index.html` (or copy the contents into the repository's root `index.html`).
2. Upload `manifest.webmanifest`, `sw.js`, `icon-192.png`, and `icon-512.png` into the same published folder as `index.html`.
3. Commit all files and wait for GitHub Pages to finish publishing.
4. Open the Pages URL in Chrome. Use Chrome menu (⋮) → **Add to Home screen** or **Install app**.
5. After changes, if an old version stays cached, close the installed app and reload the site; clear site data if needed.

## Build an Android APK (requires a computer)
This ZIP is not a signed APK. Build tools and Android SDK are required.
1. Install a current Node.js LTS release and Android Studio on a computer.
2. Unzip this bundle and open a terminal in the unzipped folder.
3. Run:
   ```sh
   npm install
   npx cap add android
   npx cap sync android
   npx cap open android
   ```
4. In Android Studio, wait for Gradle sync. Test on a physical Android device, including microphone permission, recording, audio import, WAV export, and MP3 export.
5. For a test APK, use **Build → Build Bundle(s) / APK(s) → Build APK(s)**. For release, create a signed APK/AAB using Android Studio's signing flow and protect the signing key.
6. If you edit `www/index.html` or any web assets, run `npx cap sync android` again before rebuilding.

## Current implementation status
Functional in the browser where supported: microphone recording, audio import/playback, multitrack timeline and WAV rendering, MP3 conversion via an online encoder, live pitch tuner, drum machine, and full project archive export/import. Browser permissions and device performance vary; test on the target phone.

Not built into this bundle: automatic vocal pitch correction/Auto-Tune, AI music generation, AI stem separation, AI mastering, account-based cloud backups, real-time collaboration, and an actual signed Android APK/AAB. The AI/cloud UI needs a secure compatible backend. Do not put API secrets in the HTML file. The live tuner identifies notes; it does not retune vocals.

## Security and reliability
- Use HTTPS for GitHub Pages and backend endpoints.
- Audio and project archives may be large; keep separate backups.
- Do not upload unreleased recordings to a service unless you trust its privacy and retention terms.
- Service worker caches the app shell only; audio assets and remote AI/MP3 services still require connectivity.
