# தமிழ் வேதாகமம் — 300 நாள் வாசிப்புத் திட்டம்

Static, mobile-first reading tracker for GitHub Pages. No backend, account, build step, or API key.

## Files
- `index.html` — app shell
- `styles.css` — responsive theme and layout
- `app.js` — progress, notes, calendar, settings, import/export
- `reading-plan.js` — 300 schedule records extracted from the supplied PDF text
- `manifest.json`, `service-worker.js` — optional install/offline support
- `assets/` — app icons

## Source accuracy and Tamil text
The original PDF's embedded/extracted Tamil text contains OCR spacing and character errors. Book names and obvious spacing errors in reading references have been normalized where possible. To avoid displaying broken Tamil or inventing a sentence and falsely attributing it to the PDF, spiritual reflections are left blank in the app until they can be transcribed and proofread from the page images. Chapter references should still be cross-checked against the original PDF before relying on the plan; this generated version is not represented as a complete human-verified transcription.

## Run locally
Open `index.html` in a browser. Service workers/PWA installation require HTTPS or localhost; all normal tracker functions can be tried without a server.

## Publish on GitHub Pages
1. Create a GitHub repository, e.g. `tamil-bible-tracker`.
2. Upload the contents of this folder (not the outer ZIP) to the repository root. Ensure `index.html` is at the root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/(root)`, then Save.
5. Wait for GitHub Pages to publish. Open the URL shown in Settings → Pages. Project URLs use `/repository-name/`; this app uses relative paths (`./`) to support that.
6. On Android Chrome, open the published HTTPS URL, tap the browser menu (⋮), then **Add to Home screen** or **Install app** if offered.
7. To update, upload/commit changed files. The app updates on next visit; the service worker replaces its cache version when `service-worker.js` changes. LocalStorage progress is separate from site files and should remain, but export a JSON backup before major changes.

## Progress and privacy
Progress, completion dates, notes, prayer, verse reference, theme and start date are stored in browser `localStorage` on this device/browser. Nothing is sent to a server by the app. Browser data clearing or switching devices can remove/miss this data, so use **Settings → JSON export** regularly. Imported JSON is validated before it replaces the saved state.

## Feature/test checklist
- [x] Static HTML/CSS/vanilla JS; no backend or build step
- [x] Day list, search, filters, completion toggle, notes/reflection fields
- [x] LocalStorage persistence, JSON export/import, reset confirmation
- [x] Start date and date-driven plan day
- [x] Progress %, completed count, remaining count, streaks, estimated minutes
- [x] Monthly calendar, light/dark theme, responsive small-screen styles
- [x] Relative paths and optional service worker cache
- [ ] Automated browser/device tests were not run in this environment
- [ ] Every schedule row and reflection has **not** been visually verified against all PDF page images; see source accuracy note


## English version and daily notes
The interface and book labels are in English. Each day includes a simple personal-notes prompt: “What did I learn today?” The notes are private to this browser's LocalStorage and are not sent to a server. Because the source PDF's Tamil OCR has errors, verify any schedule entry flagged as uncertain against the PDF before relying on it.
