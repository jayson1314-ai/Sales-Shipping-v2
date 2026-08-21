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

`index.html` contains a static JSON snapshot of item data (carton qty,
weight, dimensions, brand, OE No.) pulled from the EMAS Pick List workbook
(Table145, Mesurement, Item Reference List, OE Reference tabs). It is
**not** live-linked to Murho/INVENTORY. Ask Claude to regenerate `index.html`
whenever new SKUs or dimensions are added to those reference sheets, then
commit and push the updated file to redeploy.

## Local preview

```bash
npx serve .
```
