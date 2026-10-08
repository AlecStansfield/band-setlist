# Band Set List — offline iPad web app

## What it does
- Large, bold song titles; tap one to reveal its notes and tap another to switch.
- Add/edit/delete songs and reorder them.
- Automatically saves the list in the browser on this iPad.
- Export/import a JSON backup.
- Caches the app shell for offline use after the first successful online visit.

## Important
A web app with a service worker must be served from HTTPS (or localhost). Opening `index.html` directly from the Files app is not the intended installation route. The easiest iPad-only route is to upload these three files to a static HTTPS host, then open the URL in Safari.

## Easiest route: GitHub Pages
1. On the iPad, download and unzip `band-setlist-pwa.zip` in Files.
2. In Safari, sign in to GitHub or create an account at https://github.com.
3. Create a new repository, for example `band-setlist`.
4. Use the repository's Add file / Upload files option and upload `index.html`, `manifest.webmanifest`, and `sw.js` from the unzipped folder. Commit the changes.
5. In the repository, open Settings → Pages. Under Build and deployment, choose Deploy from a branch, select the `main` branch and `/ (root)`, then Save.
6. Wait for GitHub Pages to publish. The URL will look like `https://YOUR-USERNAME.github.io/band-setlist/` (replace YOUR-USERNAME with your GitHub username).
7. Open that URL in Safari on the iPad while online. Wait a few seconds, then reload once so the service worker can take control.
8. Use Share → Add to Home Screen. If shown, leave Open as Web App enabled. Tap Add.
9. Open the new Home Screen icon while still online once. Add a test song, close the app, reopen it and check the song remains.
10. Enable Airplane Mode and open the Home Screen app. Check that songs, editing and notes still work. Only rely on it at a gig after this test succeeds.

## Using the app
- Tap a song title to show/hide its notes. Tapping another song replaces the visible notes.
- Tap Add song to create a song.
- Tap Edit list to reveal Edit, Move up, Move down and Delete controls.
- Tap Export backup and save `band-setlist-backup.json` to Files or iCloud Drive.
- Tap Import backup to restore a previous JSON backup. Import replaces the current list, so export first if needed.

## Privacy and data
The app does not send your song titles or notes to a server. They are stored in local browser storage on that iPad. A backup file is separate from the app and should be kept somewhere safe. Clearing Safari website data or removing browser data may erase the local list.

## Updating the app
If you later replace the app files on the host, increase the `CACHE_NAME` in `sw.js` (for example, `band-set-list-v2`) and reload the app online to ensure the new version is cached.
