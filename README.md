# Peli Planner

A single-page planner for laying out Pelican case TrekPak dividers. Pick a case, list your gear, draw or auto-arrange divider runs, check fit and weight, and see which case you need.

No build step and no dependencies. It is one `index.html` plus a favicon. Fonts load from Google Fonts and fall back to system fonts if blocked.

## Publish on GitHub Pages

1. Create a new GitHub repository (public, or private if your plan supports Pages on private repos).
2. Upload everything in this folder to the repository root: `index.html`, `favicon.svg`, `.nojekyll`, `README.md`.
3. In the repository go to **Settings > Pages**.
4. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose **main** and **/ (root)**, then Save.
5. After a minute the site is live at `https://<your-username>.github.io/<repo-name>/`.

With the GitHub CLI:

```bash
git init -b main
git add .
git commit -m "Peli Planner"
gh repo create peli-planner --public --source=. --push
gh api -X POST repos/:owner/peli-planner/pages -f "source[branch]=main" -f "source[path]=/"
```

## Notes

- Your plan and gear library are saved in the visitor's own browser (localStorage), per site address. They are not shared between devices or people. Use **Copy library** and **Import** on the Gear library tab to move a library.
- Interior case sizes come from Pelican's TrekPak case list. The planning grid is not TrekPak's real pin spacing, so check a layout against the actual panels before buying or cutting anything.
- This is an independent planning tool and is not made or endorsed by Pelican.
