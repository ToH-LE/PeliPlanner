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

## Live sync from a Google Sheet

The Gear library tab can keep itself up to date from a Google Sheet that you publish as a CSV.

1. Create a sheet with the headings in `gear-library-template.csv` (File > Import works with a CSV from this page's Export CSV). Put units in the headings, for example `Length (mm)` and `Weight (kg)`.
2. In Google Sheets choose **File > Share > Publish to web**, pick the sheet tab, choose **Comma-separated values (.csv)** and publish. Copy the link.
3. In the app open **Gear library > Live sync from a Google Sheet**, paste the link and choose **Sync now**.

The app then checks again when you open it, when you come back to the tab, and every five minutes, or whenever you choose Sync now. Items are matched by name. The sheet updates the size, weight, category and notes of matching items, adds new ones, and leaves items you added in the app alone unless you tick **Remove items that are not in the sheet**.

To give every visitor the same sync without pasting the link, put it in `DEFAULT_SYNC_URL` near the top of the script in `index.html`.

Publishing to the web makes the whole sheet readable by anyone with the link, so keep anything private out of it. You can stop publishing from the same dialog. Google can take a few minutes to show an edit. Each browser stores its own sync link and library.

## Plans (save, switch, import, export)

The **Plan** menu above the case lets you keep several layouts and flick between them. Every change autosaves to the current plan. Use **New plan**, **Save as copy** (duplicates and switches to the copy), **Delete plan**, **Export plan** / **Export all** (JSON files) and **Import** (choose a file or paste its text). Plans are stored in this browser; export them to back up or move to another device.

## Notes

- Your plan and gear library are saved in the visitor's own browser (localStorage), per site address. They are not shared between devices or people. On the Gear library tab, **Export CSV** saves the library as a file Excel and Google Sheets open directly, and **Import** reads a CSV back in. Put units in the column headings, for example `Length (mm)` and `Weight (kg)`. Import adds new items and updates items with the same name, or replaces the whole library if you choose.
- Empty case weights (no foam) come from Pelican's published catalogs and product pages. They do not include TrekPak dividers.
- Interior case sizes come from Pelican's TrekPak case list. The planning grid is not TrekPak's real pin spacing, so check a layout against the actual panels before buying or cutting anything.
- This is an independent planning tool and is not made or endorsed by Pelican.
