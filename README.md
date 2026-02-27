# State Tax Comparison App

Single-page web app for comparing **state + local tax revenue** across states for one year in **nominal dollars**.

## Current status

- React + Vite scaffold complete
- Starter dashboard complete (total + per-capita comparisons)
- First-pass ingestion pipeline complete
- Sample dataset included for UI development

## Quick start

```bash
npm install
npm run dev
```

The app loads:

1. `public/data/state-tax-summary-2023.json` (generated)
2. fallback: `public/data/state-tax-summary-sample.json`

## Ingest real data

1. Configure source URLs and aliases in `data/config/source-download.config.json`
2. Run one command:

```bash
npm run data:refresh
```

This command performs:

- `data:download` (download source CSVs)
- `data:normalize` (map source columns into canonical raw files)
- `data:ingest` (build production JSON)

## Manual fallback

If you already have prepared CSVs, you can skip download/normalize.

1. Add source CSV files in `data/raw`:
   - `state-local-tax-by-type.csv`
   - `state-population.csv`
2. If needed, adjust `data/config/ingestion.config.json`
3. Run:

```bash
npm run data:ingest
```

Generated output:

- `public/data/state-tax-summary-2023.json`

## Source guidance

See `scripts/source-catalog.md` for the primary source list and expected schema.
