# Business Performance & Revenue Analytics Dashboard

Interactive admin dashboard for tracking **leads, quotations, deals, orders and payments** with full filtering, period-over-period comparison and drill-down views.

Built as a **pure static front-end** (HTML + CSS + vanilla JS). No build step, no backend, no database.

## Files

| File | Purpose |
|---|---|
| `index.html` | Whole dashboard — layout, styles and application logic in one file |
| `vendor/chart.umd.min.js` | Chart.js 4.4.1 (included so charts work offline; CDN used as fallback) |

## Run locally

Just open `index.html` in a browser — or serve it:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

## Features

- **Lead Analytics** — KPI cards (total / qualified / converted / unqualified / conversion rate), target achievement, lead funnel, daily lead trend, lead sources.
- **Quotation Analytics** — quotations by service, quotation value by service, service-wise detail table, quote-to-deal conversion gauge.
- **Deals & Revenue** — deals vs revenue by service, revenue by category, priority breakdown, daily revenue trend, total vs collected vs outstanding revenue, collection rate.
- **Orders & Payments** — order status, orders & stage progress by service, payment history, cumulative collection trend.
- **Teams** — sales team activity, operations team activity, deal progress, recent CRM activity feed.
- **Filters** — Today / Last 7 Days / Last 30 Days / Custom date range, plus user and department filters. Every card, chart and table updates with the filters.
- **Period comparison** — every KPI shows the % increase/decrease against the equal-length previous period (green = favourable, red = unfavourable).
- **Drill-downs** — click any KPI card, chart segment, bar, table row or activity item to open a detail modal (lead → quotations → deals → orders → payments).
- **Export** — Export button downloads the filtered leads as CSV.

## Data

All data is **dummy data**, generated deterministically in the browser (seeded random) over the last 120 days, so the numbers stay stable between reloads. Model relationships: one lead → many quotations and deals → one deal → many orders and payments.

To point it at a real backend, replace the seeded generation block at the top of the `<script>` section in `index.html` with a fetch to your API — everything downstream reads from the `leads / quotations / deals / orders / payments` arrays.

## Deploy — get a public URL

### GitHub Pages (free, permanent)

```bash
git init
git add .
git commit -m "Add business analytics dashboard"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

Then in the repository: **Settings → Pages → Source: Branch `main` / folder `/ (root)` → Save**.
Your site appears at `https://<your-username>.github.io/<repo-name>/` within a minute.

### Any other static host

The folder can be uploaded as-is to Netlify Drop, Cloudflare Pages, Vercel, Render Static, or any web server — `index.html` is at the root.
