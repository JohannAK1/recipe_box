# Recipe Box — offline recipe app for iPhone

A web app you install to your home screen. Recipes (including photos) are stored
**only on your iPhone** (IndexedDB). It works offline after the first visit.

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
- **+** adds a recipe; tap a recipe to view, **Edit** to change it.
- Ingredients: one per line, starting with the amount (`200 g flour`, `1/2 tsp salt`,
  `2-3 eggs`) so they scale when you change servings. A line ending in `:` becomes a heading.
- Tap ingredients to tick them off while cooking.
- Search covers titles, tags and ingredients; tags become filter chips.

## 4. Backups (important)
Data lives only on the phone. If you delete the home-screen app, the recipes go with it.
Tap the **share icon** (top right of the list) → **Export backup** and save the file to
Files / iCloud Drive now and then. **Import backup** restores it (also on a new phone).

## 5. Changing the app with Claude
Ask Claude for a change, replace the files in your repository, and **bump the version
in `sw.js`** (`recipe-box-v1` → `recipe-box-v2`). Open the app twice on the phone to
pick up the update. Your recipes are not affected by updates.
