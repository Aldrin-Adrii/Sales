# Sales
# SalesIQ — Sales Analytics Dashboard

A fully client-side sales analytics dashboard built as a single HTML file. Add products with monthly unit data, and every chart, KPI, and table updates instantly — no server, no database, no build step needed.

---

## Overview

SalesIQ is an interactive data entry + visualization tool aimed at small business owners, sales teams, or analysts who want to explore product performance without setting up any infrastructure. All data lives in memory for the session and can be exported as CSV at any time.

It ships with four demo products preloaded (Wireless Headphones, Cotton T-Shirt, Smart Watch, Premium Coffee) so the dashboard is never empty on first open.

---

## Features

### Data Entry (Sidebar)
- Add unlimited products with name, category, unit price, and region
- Enter monthly units sold for all 12 months (Jan – Dec) per product
- Products appear as pills in a scrollable sidebar list with one-click removal
- Clear All button wipes the entire dataset
- Input validation with toast notifications for missing or invalid fields

### KPI Cards (4 metrics, always visible)
- **Total Revenue** — sum of all product revenues, formatted in K / L / Cr
- **Total Units Sold** — aggregate across all products and months
- **Best Seller** — product with highest revenue
- **Average Order Value** — total revenue ÷ total units

### Charts (4 visualisations, all reactive)
- **Monthly Revenue Trend** — multi-line Chart.js chart, one line per product, Jan–Dec
- **Sales by Category** — donut chart grouping revenue by category
- **Units Sold by Product** — horizontal or vertical bar chart (auto-switches axis when >4 products)
- All charts show a friendly placeholder when no products are added

### Performance Table
- Sortable by revenue (highest first)
- Columns: rank, product name + category + region, units sold, total revenue, revenue share bar
- Rank #1 highlighted with a red badge

### Regional Breakdown
- Bar breakdown of total revenue per region (North / South / East / West / Central / International)
- Each region colour-coded consistently across the app
- Revenue amount and percentage displayed alongside each bar

### Utility
- **Export CSV** — downloads `salesiq-export.csv` with all product data (name, category, region, unit price, total units, total revenue)
- **Live timestamp** — top-right clock updates every minute, formatted for Indian locale
- **Toast notifications** — non-blocking feedback for add, remove, clear, and export actions
- **Grain texture overlay** — subtle SVG noise over the warm off-white background

---

## Language Stack

| Language | Lines | Percentage |
|----------|-------|------------|
| JavaScript | 412 | 47.9% |
| HTML | 181 | 21.0% |
| CSS | 266 | 30.9% |
| TypeScript | 0 | 0% |
| **Total** | **859** | |

---

## Fonts

| Font | Usage |
|------|-------|
| Syne (400–800) | Brand name, page title, chart titles, buttons |
| Epilogue | Body text, labels, table content |
| JetBrains Mono | KPI values, timestamps, revenue figures |

All fonts loaded via Google Fonts CDN — no install needed.

---

## External Dependencies

| Library | Version | Purpose | Load method |
|---------|---------|---------|-------------|
| Chart.js | 4.4.1 | Line, donut, and bar charts | CDN |

No other dependencies. No npm, no bundler, no framework.

---

## Layout Structure

```
┌─────────────────────────────────────────────────┐
│  Sidebar (300px)        │  Main content area     │
│  ─────────────          │  ──────────────────    │
│  Brand logo             │  Topbar + timestamp    │
│  Add product form       │  4 KPI cards           │
│  Monthly inputs (12)    │  Revenue line chart    │
│  Add button             │  Category donut chart  │
│  Product pills list     │  Units bar chart       │
│                         │  Performance table     │
│                         │  Regional breakdown    │
│                         │  Footer                │
└─────────────────────────────────────────────────┘
```

---

## Design Tokens

```css
--bg:       #f5f3ee   /* warm off-white page background  */
--surface:  #ffffff   /* card / panel surfaces            */
--surface2: #f0ede6   /* secondary / hover surfaces       */
--border:   #e2ddd5   /* dividers and card borders        */
--ink:      #1a1714   /* primary text, sidebar background */
--muted:    #8a8279   /* secondary text, chart labels     */
--accent:   #c84b31   /* primary red — CTA, highlights    */
--accent2:  #e8a838   /* amber — secondary accent         */
--accent3:  #2d6a4f   /* green — positive / growth        */
--accent4:  #3a6186   /* blue — fourth data series        */
```

---

## Colour System

### Product colours (assigned in order, cycling)
```
#c84b31  #e8a838  #2d6a4f  #3a6186
#7b5ea7  #c8963b  #1a7a6e  #c84b6e
```

### Region colours (fixed per region)
| Region | Colour |
|--------|--------|
| North | `#c84b31` |
| South | `#e8a838` |
| East | `#2d6a4f` |
| West | `#3a6186` |
| Central | `#7b5ea7` |
| International | `#1a7a6e` |

---

## Revenue Number Formatting

All monetary values use a compact Indian number format:

| Value range | Format | Example |
|-------------|--------|---------|
| ≥ 1,00,00,000 | Crore | `₹2.34Cr` |
| ≥ 1,00,000 | Lakh | `₹4.56L` |
| ≥ 1,000 | Thousand | `₹12.3K` |
| < 1,000 | Raw | `₹999` |

---

## Supported Categories

Electronics · Clothing · Food & Beverage · Home & Living · Software · Services · Other

---

## Supported Regions

North · South · East · West · Central · International

---

## Setup

No setup required — just open the file in any browser.

```bash
# Option 1 — double-click the file
open sales-dashboard.html

# Option 2 — serve locally if needed
npx serve .
# or
python3 -m http.server 8080
```

### Removing the demo data

The dashboard preloads 4 demo products on first open. To start blank, open the file and comment out or remove this line near the bottom of the `<script>` block:

```js
loadDemoData(); // Comment this out to start with empty dashboard
```

---

## CSV Export Format

The Export CSV button downloads a file named `salesiq-export.csv` with the following columns:

```
Product, Category, Region, Unit Price, Total Units, Total Revenue
```

Example:
```csv
Product,Category,Region,Unit Price,Total Units,Total Revenue
"Wireless Headphones","Electronics","South",2999,327,979673
"Cotton T-Shirt","Clothing","North",599,925,554075
```

---

## Responsive Behaviour

| Breakpoint | Changes |
|------------|---------|
| > 900px | Sidebar fixed at 300px, 4-column KPI grid, 2-column charts |
| ≤ 900px | Sidebar collapses to top (stacks vertically), KPI grid becomes 2-column, all charts stack to single column |

---

## Browser Support

Works in all modern browsers — Chrome, Firefox, Safari, Edge. No polyfills required.

---

## License

Free to use and modify for personal or commercial projects.
