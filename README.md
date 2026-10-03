# Recipe Box — offline recipe app for iPhone

A web app you install to your home screen. Instead of typing recipes in, you save
**links to the original recipes** plus your own **notes** (and optional tags/photo).
Everything is stored **only on your iPhone** (IndexedDB). The app opens offline; the
linked recipe pages themselves need internet.

## Files
| File | Purpose |
|---|---|
| `index.html` | The whole app (screens, styles, logic, storage) |
| `sw.js` | Service worker — caches the app so it runs offline |
| `manifest.json` | App name, icon, standalone display |
| `icon-*.png`, `apple-touch-icon.png` | Home-screen icons |

## 1. Put it online (free, one time)
The iPhone needs to load the files once over **HTTPS**. The hosting only serves the
app's code — your recipes never leave the phone.

**GitHub Pages (recommended)**
1. Create a free account at github.com and a new **public** repository, e.g. `recipe-box`.
2. "Add file → Upload files", drag in all files from this folder, commit.
3. Settings → Pages → Source: *Deploy from a branch* → Branch `main`, folder `/ (root)` → Save.
4. After a minute your app is at `https://<your-username>.github.io/recipe-box/`.

(Netlify or Cloudflare Pages work too — drag-and-drop the folder.)

## 2. Install on the iPhone
1. Open the URL in **Safari**.
2. Tap **Share → Add to Home Screen → Add**.
3. From now on, open it **from the home-screen icon**. The installed app has its
   own storage, separate from Safari tabs — so add your recipes there.

## 3. Using it
- Copy a recipe's link (e.g. Safari → Share → Copy), open the app, tap **+**, then **Paste**.
- Title is optional — if you leave it empty, the website name is used.
- **Notes**: your changes, tips, how it turned out. Notes are searchable.
- In a recipe, **Open recipe ↗** opens the original page; **Share link** sends it on.
- Search covers titles, notes, tags and websites; tags become filter chips.
- Recipes saved with the older version keep their ingredients and steps (shown read-only).

## 4. Backups (important)
Data lives only on the phone. If you delete the home-screen app, the recipes go with it.
Tap the **share icon** (top right of the list) → **Export backup** and save the file to
Files / iCloud Drive now and then. **Import backup** restores it (also on a new phone).

## 5. Changing the app with Claude
Ask Claude for a change, replace the files in your repository, and **bump the version
in `sw.js`** (`recipe-box-v1` → `recipe-box-v2`). Open the app twice on the phone to
pick up the update. Your recipes are not affected by updates.
