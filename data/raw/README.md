# Raw data drop zone

Place your source CSV files here before running ingestion:

- `state-local-tax-by-type.csv`
- `state-population.csv`

Then run:

```bash
npm run data:ingest
```

Output file:

- `public/data/state-tax-summary-2023.json`
