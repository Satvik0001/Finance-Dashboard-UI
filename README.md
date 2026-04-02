# Fintrek — Finance Dashboard

A clean, interactive personal finance dashboard built with vanilla JavaScript, Chart.js, and a custom dark design system. No build tools required.

---

## Quick Start

```bash
# Just open in a browser — no server needed
open finance-dashboard.html

# Or serve locally for best results
npx serve .
# Then visit http://localhost:3000/finance-dashboard.html
```

---

## Features

### Dashboard Overview
- **4 Summary Cards** — Total Balance, Income, Expenses, and Savings Rate, each with color-coded accent lines and trend indicators
- **Balance Trend Chart** — Bar chart showing monthly income vs expenses with 3 period filters (1M / 3M / 6M)
- **Spending Breakdown Donut** — Categorical donut chart with live legend showing % split per category
- **Recent Transactions** — Quick-view of 5 most recent entries

### Transactions
- **Full transaction table** with description, category badge, date, type pill, and amount
- **Real-time search** — filters by description or category as you type
- **Multi-filter support** — filter by Type, Category, Month
- **Sort** by date (newest/oldest) or amount (high/low)
- **Pagination** — 10 transactions per page with smart page number rendering
- **Empty state** when no results match filters

### Role-Based UI
Switch roles via the sidebar dropdown:
- **Admin** — Can add and edit transactions; sees the "Add Transaction" button and inline edit icons
- **Viewer** — Read-only mode; all write actions are hidden

Role selection is persisted via `localStorage`.

### Insights
- **6 Insight Cards** — Top spending category, Best month, Average monthly spend, Profitable months count, Savings rate, Net balance
- **Monthly Comparison** line chart — Income vs Expenses overlay across all 12 months
- **Category Spend** horizontal bar chart — Top 7 expense categories ranked by total
- **Cumulative Balance** area chart — Running balance progression across the year

### State Management
All state is managed in vanilla JS global variables:
- `transactions[]` — full transaction list
- `currentRole` — active role string
- `currentPage` — pagination state
- `currentPeriod` — selected chart time range

Filters are read directly from DOM inputs during `renderTransactions()`, avoiding stale state bugs.

### Data Persistence
All transactions and role selection are saved to `localStorage` under the keys:
- `fintrek_tx` — JSON array of transactions
- `fintrek_role` — current role string

Data survives page refreshes. 12 months of realistic seed data is auto-generated on first load.

### Export
The Export button downloads a CSV of the currently filtered transaction view (not the full dataset), so exports respect your active filters.

---

## Tech Stack

| Concern       | Choice                          |
|---------------|---------------------------------|
| Framework     | Vanilla JS (no build step)       |
| Charts        | Chart.js 4.4.1 (CDN)            |
| Fonts         | DM Sans + DM Serif Display (Google Fonts) |
| Storage       | localStorage                    |
| Styling       | Pure CSS with CSS custom properties |
| Icons         | Inline SVG                      |

---

## Design Decisions

**Dark-first aesthetic** — Finance UIs are often used late at night or in low-light conditions. The dark palette (`#0d0f14` base) reduces eye strain while maintaining high contrast ratios.

**DM Serif Display for headings** — Adds warmth and editorial character to a data-heavy interface, avoiding the sterile feel of purely sans-serif finance dashboards.

**Category color system** — Each category has a fixed color used consistently across all charts, badges, and legend items, helping users build a mental model without relying on labels alone.

**Donut with centered total** — Provides at-a-glance "total expenses" context while the segments show relative breakdown.

**No build tools** — A single HTML file keeps the submission self-contained and opens directly in any browser. All dependencies are loaded from CDN.

---

## Assumptions Made

- Data is for the year **2024**
- "Balance" is computed as `Total Income − Total Expenses` (not a bank account balance)
- Savings rate = `(Balance / Income) × 100`
- Seed data is auto-generated with realistic variance across 12 months (~80 transactions)
- The "Viewer" role restriction is frontend-only, as per the assignment's RBAC simulation requirement

---

## Optional Enhancements Implemented

- ✅ Dark mode (native, always-on)
- ✅ Data persistence via localStorage
- ✅ Export to CSV
- ✅ Animations and transitions (card hover lift, modal scale-in, toast slide-up)
- ✅ Responsive layout with hamburger sidebar on mobile
- ✅ Empty state handling
- ✅ Pagination

---

## File Structure

```
finance-dashboard.html   # Single-file application
README.md                # This file
```
