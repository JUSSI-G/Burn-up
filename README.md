# Burn-up Tool

A lightweight, no-build sprint burn-up chart for agile teams. Enter incremental scope and completed points per sprint and watch the chart update live.

## What it does

- Tracks **cumulative scope** (orange step line) and **cumulative completed points** (teal line) across sprints
- Scope can grow mid-project — the step-after chart style makes scope increases visible immediately
- Add or remove sprints dynamically; summary totals update in the header

## Running locally

Because `app.js` is loaded via Babel standalone (which uses `fetch`), the page must be served over HTTP opening `index.html` directly as a file will not work.

Any static file server works. Pick whichever is most convenient, for example:

```bash
# Node.js (npx, no install needed)
npx serve .

# Python 3
python -m http.server 8080
```

Then open `http://localhost:5000` (npx serve) or `http://localhost:8080` (Python) in your browser.

## Project structure

```
burn-up/
├── index.html    # HTML shell and CDN script tags
├── styles.css    # Custom CSS (base styles not covered by Tailwind)
├── app.js        # React app and chart logic (JSX, transformed by Babel in-browser)
└── README.md
```

## Dependencies (all via CDN, no install required)

| Library | Version | Purpose |
|---|---|---|
| React | 18.2.0 | UI framework |
| ReactDOM | 18.2.0 | DOM rendering |
| PropTypes | 15.8.1 | Required by Recharts |
| Recharts | 2.12.7 | Chart components |
| Babel Standalone | latest | In-browser JSX transform |
| Tailwind CSS | latest | Utility-first styling |

Recharts and React versions are pinned to avoid breaking changes. Tailwind and Babel are pulled at latest since they are dev/rendering utilities only.

## How to use

1. Start with the default three sprints or add more with **Add Sprint**
2. For each sprint, enter:
   - **New Scope**: story points added to the backlog *this sprint* (incremental, not cumulative)
   - **Pts Done**: story points completed *this sprint* (incremental, not cumulative)
3. The chart and header totals update instantly
4. Hover over the chart for exact values per sprint
5. Delete a sprint by hovering its row and clicking the trash icon (minimum 1 sprint enforced)
