# EMAS Sales M3 Calculator

Standalone sales tool: enter EMAS P/N + Qty, get auto carton count, weight,
and shipping volume (M3) with pallet estimates. Pure static HTML/CSS/JS —
no server, no build step. The item lookup database (~7,300 SKUs) is baked
into `index.html`.

## Deploy to Vercel via GitHub

1. Push this folder to a new GitHub repo:
   ```bash
   cd emas-sales-m3-calculator
   git init
   git add .
   git commit -m "Initial commit: EMAS Sales M3 Calculator"
   git branch -M main
   git remote add origin https://github.com/<your-org>/emas-sales-m3-calculator.git
   git push -u origin main
   ```
2. Go to [vercel.com/new](https://vercel.com/new), import the GitHub repo.
3. Framework preset: **Other** (static site). No build command, no
   output directory override needed — Vercel will serve `index.html` as-is.
4. Click **Deploy**. You'll get a live URL (e.g. `emas-sales-m3-calculator.vercel.app`).

Every future push to `main` auto-redeploys.

## Updating the item database

`index.html` ships with a baked-in JSON snapshot of item data (carton qty,
weight, dimensions, brand, OE No.), and it is **not** live-linked to
Murho/INVENTORY. Two ways to refresh it:

**Self-service (no need to come back to Claude):** open the deployed site,
use the **Item Database** card at the top, and upload the EMAS Pick List
workbook (or just the updated Table145 / Mesurement / Item Reference List /
OE Reference tabs) — it's parsed right in the browser with SheetJS and saved
to that browser's local storage. New/changed P/Ns override the baked-in
snapshot; anything not in the upload keeps its original value. This only
persists on the device/browser that did the upload — repeat it on each
device your team uses, or re-upload after clearing browser data. "Revert to
Original Snapshot" clears the override and reloads the file's baked-in data.

**Baked into the file:** ask Claude to regenerate `index.html` from an
updated workbook, then commit and push — this updates the snapshot for
everyone by default, with no per-browser upload needed.

## Local preview

```bash
npx serve .
```
