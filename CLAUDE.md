# LynxApps Portfolio Site

Static GitHub Pages site (no build step) for LynxApps — privacy-first iOS apps. Plain HTML/CSS/JS, no framework, no bundler.

**Live site:** https://khsalman.github.io

## Structure

- `index.html` — homepage, lists all apps as cards in `#apps` (grid `.apps-grid`)
- `<app-slug>/index.html` — each app's landing page
- `<app-slug>/privacy/index.html`, `<app-slug>/terms/index.html`, `<app-slug>/support/index.html` — required sub-pages per app
- `<app-slug>/appstore-qr.svg` — self-hosted QR code SVG once an app is live (see QR codes below)
- `assets/css/lynx.css` — single shared stylesheet for every page
- `assets/js/lynx.js` — shared JS: mobile nav toggle + scroll-reveal (`.reveal` → `.in`)
- `svg/` — shared logo/lockup/favicon assets

Every app page is self-contained HTML with this layout: `site-header` (nav with `← All apps` / `← <App>`, sub-page links, `nav-cta`) → `hero` → feature/pricing sections → `cta` (download/notify section) → `site-footer`.

## App inventory

| Slug | Name | Status | App Store URL |
|---|---|---|---|
| `duplicate-photo-finder` | Duplicate Photo Finder | ✅ Live | https://apps.apple.com/us/app/duplicate-photo-finder/id6774906761 |
| `receipt-digitizer` | Receipt Digitizer | ✅ Live | https://apps.apple.com/us/app/receipt-digitizer/id6771928139 |
| `vow` | Vow | ✅ Live | https://apps.apple.com/us/app/vow-commitment-tracker/id6777075479 |
| `inspectkit` | InspectKit Site Reports Pro | ✅ Live | https://apps.apple.com/us/app/inspectkit-site-reports-pro/id6782454914 |
| `reefdose` | ReefDose | ✅ Live | https://apps.apple.com/us/app/reefdose-dosing-calculator/id6782320223 |
| `honestfast` | Honest Fast | ✅ Live | https://apps.apple.com/us/app/honest-fast-track-your-fasts/id6786001645 |
| `homelogbook` | Home Logbook | ✅ Live | https://apps.apple.com/us/app/home-logbook/id6786788852 |
| `renewaldesk` | RenewalDesk | ✅ Live | https://apps.apple.com/pk/app/renewaldesk/id6787748262 |
| `closingdesk` | ClosingDesk | ✅ Live | https://apps.apple.com/pk/app/closingdesk/id6787710712 |
| `pillvault` | PillVault | ⏳ In App Review | — |
| `microhabit-physics` | MicroHabit Physics | ⏳ In App Review | — |
| `subguard` | SubGuard | ⏳ In App Review | — |
| `orvia` | Orvia | 🔧 Under Development | — |
| `propertynest` | PropertyNest | 🔧 Under Development | — |
| `halalcheck` | HalalCheck | 🔧 Under Development | — |
| `zakatbook` | Zakat Book | ✅ Live | https://apps.apple.com/us/app/zakat-book/id6789597763 |

**Homepage card order:** Live apps first, then In App Review, then Under Development. Update DOM order (not just CSS) when status changes.

**Homepage app count headline:** Keep `index.html`'s "N tools, one philosophy" h2 in sync when adding apps (currently: **Sixteen**).

## Per-app theming

Each app gets a `data-theme="<key>"` attribute on `<html>`, which maps to CSS vars in `lynx.css`:

```css
[data-theme="photo"]       { --g1:#6366f1; --g2:#8b5cf6; --accent:#6d5dfb; --accent-soft:#eef0ff; --accent-border:#e0e3ff; }
[data-theme="pill"]        { --g1:#0ea5e9; --g2:#14b8a6; --accent:#0d9488; --accent-soft:#ecfeff; --accent-border:#cffafe; }
[data-theme="receipt"]     { --g1:#f59e0b; --g2:#f97316; --accent:#ea7317; --accent-soft:#fff7ed; --accent-border:#fed7aa; }
[data-theme="vow"]         { --g1:#7c3aed; --g2:#db2777; --accent:#7c3aed; --accent-soft:#faf5ff; --accent-border:#e9d5ff; }
[data-theme="mhp"]         { --g1:#0ea5e9; --g2:#06b6d4; --accent:#0284c7; --accent-soft:#cffafe; --accent-border:#a5f3fc; }
[data-theme="inspectkit"]  { --g1:#1B4FBF; --g2:#00C4FF; --accent:#1B4FBF; --accent-soft:#E3F2FD; --accent-border:#90CAF9; }
[data-theme="orvia"]       { --g1:#5856D6; --g2:#A855F7; --accent:#5856D6; --accent-soft:#F1F0FE; --accent-border:#D9D6FB; }
[data-theme="subguard"]    { --g1:#10b981; --g2:#0d9488; --accent:#059669; --accent-soft:#ecfdf5; --accent-border:#a7f3d0; }
[data-theme="reefdose"]    { --g1:#0891b2; --g2:#06b6d4; --accent:#0284c7; --accent-soft:#cffafe; --accent-border:#a5f3fc; }
[data-theme="honestfast"]  { --g1:#f97316; --g2:#d4a017; --accent:#ea7317; --accent-soft:#fff7ed; --accent-border:#fed7aa; }
[data-theme="homelogbook"] { --g1:#2E75B6; --g2:#1e9de0; --accent:#2E75B6; --accent-soft:#eff6ff; --accent-border:#bfdbfe; }
[data-theme="closingdesk"] { --g1:#1B2345; --g2:#2d4a7a; --accent:#f2b841; --accent-soft:#fffbeb; --accent-border:#fde68a; }
[data-theme="renewaldesk"] { --g1:#4F46E5; --g2:#5956F2; --accent:#5956F2; --accent-soft:#EEF2FF; --accent-border:#C7D2FE; }
[data-theme="zakatbook"]   { --g1:#1B6B3A; --g2:#2E8B57; --accent:#1B6B3A; --accent-soft:#f0fdf4; --accent-border:#bbf7d0; }
[data-theme="propertynest"] { --g1:#7B4F2E; --g2:#C4824A; --accent:#9A5F38; --accent-soft:#FDF5EF; --accent-border:#F0D5BE; }
[data-theme="halalcheck"]   { --g1:#14532d; --g2:#16a34a; --accent:#15803d; --accent-soft:#f0fdf4; --accent-border:#bbf7d0; }
```

Homepage app cards use parallel `.theme-row-<key>` / `.grad-<key>` classes defined inline in `index.html`'s `<style>` block — keep these in sync with the per-app theme above when adding a new app.

## Adding a new app

1. Pick a theme key, add its `[data-theme="..."]` block to `lynx.css`.
2. Create `<slug>/index.html`, `<slug>/privacy/index.html`, `<slug>/terms/index.html`, `<slug>/support/index.html` following an existing app as the template (copy structure, not content).
3. Add a card to `index.html`'s `.apps-grid` with matching `.theme-row-<key>` / `.grad-<key>` CSS, plus footer links (`Apps` and `Support` columns) and increment the "N tools, one philosophy" headline.
4. Add the app to the inventory table above.
5. Status badge on the card and hero CTA on the app page must reflect real state — see Launch status below.

## Launch status — keep in sync everywhere

Each app is in one of three states, and it must read consistently across **every** page that mentions it (homepage card + badge, app landing page hero/CTA/pricing buttons, and any "Coming soon" / "Notify me" copy in sub-pages):

| State | Homepage badge | Typical copy |
|---|---|---|
| Live | `<span class="badge badge-live">Live on App Store</span>` | "Download on App Store", links to the real App Store URL, App Store QR code in the CTA |
| In App Review | `<span class="badge badge-review">In App Review</span>` | "⏳ Status: In App Review — launching soon", "Notify me at launch" mailto CTA |
| In preparation | `<span class="badge badge-review">Coming Soon</span>` or similar | "Under development" / no firm date |

When an app goes live, sweep **all** of its pages (index, privacy, terms, support) for stale references — nav CTA buttons, "Coming soon"/"Notify me"/"in App Review" copy, support-page install instructions — not just the homepage and hero section. Grep for `coming soon`, `in app review`, `notify me`, `under development` (case-insensitive) across the app's directory before considering the update done.

Also update the app inventory table above and move the homepage card to the live section.

## QR codes

When an app goes live, generate a self-hosted SVG QR code for its App Store URL — don't use an external QR API (no third-party request, crisper rendering, matches the site's offline/privacy-first ethos):

```bash
python3 -m venv /tmp/qrvenv && /tmp/qrvenv/bin/pip install segno --quiet
/tmp/qrvenv/bin/python - <<'PY'
import segno
qr = segno.make("<app-store-url>", error='h')
qr.save("<slug>/appstore-qr.svg", kind="svg", dark="#1f2937", light=None, border=2, scale=10)
PY
rm -rf /tmp/qrvenv
```

Embed it using the existing `.qr` component (white card, image + caption) inside the `.cta` section:

```html
<div class="qr">
    <img src="/<slug>/appstore-qr.svg" alt="Scan to download <App> on the App Store">
    <span>Scan with your iPhone camera</span>
</div>
```

## Git workflow

- Direct pushes to `main` are blocked by the auto-mode permission classifier (no PR review bypass). Commit normally, then push — if push is denied, the commit still succeeds; retry the push or ask the user how they want to land it.
- Co-author commits with `Co-Authored-By: Claude <model> <noreply@anthropic.com>`.
