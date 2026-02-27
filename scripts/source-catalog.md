# State + Local Tax Data Source Catalog (First Pass)

This project is currently configured for **one year** in **nominal dollars**.

## Primary sources

1. **U.S. Census Bureau — Annual Survey of State and Local Government Finances**
   - Current pipeline uses Census API endpoint for `SVY_COMP=04` (Annual Survey of State and Local Finance):
   - `https://api.census.gov/data/timeseries/govs?get=NAME,GOVTYPE,GOVTYPE_LABEL,AGG_DESC,AGG_DESC_LABEL,AMOUNT,YEAR&for=state:*&time=2023&SVY_COMP=04`
   - Normalization maps Census `AGG_DESC` tax codes to app tax categories and separates `GOVTYPE` 002 (state) vs 003 (local).

2. **U.S. Census Bureau — Annual State Population Estimates**
   - Use state population for the same reference year used by the tax file.

## Expected local CSV schema

### Tax file (`data/raw/state-local-tax-by-type.csv`)

- `state`
- `year`
- `tax_type`
- `state_tax_revenue`
- `local_tax_revenue`

### Population file (`data/raw/state-population.csv`)

- `state`
- `year`
- `population`

If your source column names differ, update `data/config/ingestion.config.json`.

## Automated refresh workflow

1. Set source URLs in `data/config/source-download.config.json`
2. Confirm alias mappings for both datasets in the same config file
3. Run:

```bash
npm run data:refresh
```

This downloads source files, normalizes them, and generates final app JSON.
