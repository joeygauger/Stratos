# Corporate Intelligence — Step 01: Company Search

This build intentionally focuses only on Step 01 of the planned product flow.

## What works now
- Live legal-entity search through the public GLEIF Global LEI Index API
- Search by company name / keyword / LEI
- Country filtering
- Entity-resolution result ranking
- Match-confidence indicator
- Legal name, LEI, country, city, entity status, LEI registration status, local registry identifier
- Explicit source provenance
- Local saved-company list using browser localStorage
- Installable PWA for iPad/iPhone

## Why this is Step 01
Every later module — company profile, financials, valuation, strategy, risk and scenarios — needs a canonical company identity. The system therefore separates the exact legal entity from a general brand name.

## Important limitations
- GLEIF is strong for legal-entity identity but is not sufficient by itself to determine stock-market listing status, ticker, ISIN, all subsidiaries, website, products or financials.
- Public/private status is intentionally left unresolved rather than guessed.
- SEC data cannot be fetched directly from a GitHub Pages browser app because data.sec.gov does not support CORS. A small backend/serverless proxy should be added in the next enrichment phase.
- Saved companies currently live only on the device/browser via localStorage.

## Upgrade on GitHub Pages
Replace the existing files in your repository with the files in this package, especially index.html, sw.js, manifest.webmanifest and the icons. Commit the changes. GitHub Pages will redeploy automatically.
