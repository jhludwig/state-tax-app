# State Tax Comparison App — Research + Implementation Plan

## Scope locked for v1

- Single reference year
- Nominal dollars only
- Top 20 states selected by that year's population
- Revenue includes combined state + local tax collections

## Research plan

- [x] Confirm tax revenue source file from U.S. Census Annual Survey of State and Local Government Finances.
- [x] Confirm population denominator source from Census annual state estimates.
- [x] Normalize source extracts into project schema.
- [ ] Validate totals with spot-checks against a secondary publication.

## Data outputs

Primary output file:

- `public/data/state-tax-summary-2023.json`

Output contains:

- Metadata (`year`, `scope`, `currency`, generation timestamp)
- Tax category definitions
- State records with totals, breakdowns, and per-capita values

## Application plan

### v1 completed scaffold

- React + Vite app
- Metric toggle: total vs per-capita
- State comparison bars
- Tax-type breakout table
- Sample dataset fallback for UI work
- Automated source downloader + normalizer pipeline

### v1 next implementation steps

- [x] Add official Census source URLs to downloader config.
- [x] Run one-command refresh and verify top-20/category mapping.
- [x] Add chart polish (stacked bars, hover tooltips, label formatting).
- [ ] Add export button for filtered table view.
- [ ] Publish as static site (GitHub Pages or Vercel).

## Validation checklist

- [x] Confirm each state's total equals sum of tax-type breakdown.
- [x] Confirm per-capita equals total divided by matching-year population.
- [x] Confirm exactly 20 states in production dataset.
- [ ] Confirm table sort and metric toggles behave as expected (logic implemented; manual UX verification pending).

## Publishing checklist

- [x] Build (`npm run build`) passes.
- [x] Production dataset file exists under `public/data`.
- [ ] Deploy static bundle and verify on mobile + desktop.
