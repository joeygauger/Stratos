# Step 1.9 — Global Security Master

This build changes the model from "company = ticker" to:

**Legal Entity → Equity Security / Share Class → Exchange Listings**

## What changed

- US issuer identity: SEC ticker/CIK index.
- US exchange recovery: SEC Submissions JSON (`data.sec.gov/submissions/...`) if the bulk ticker file does not provide an exchange.
- US OpenFIGI resolution now maps from the verified ticker instead of relying on a company-name search.
- Non-US issuers continue through global OpenFIGI name search.
- A resolved OpenFIGI Share Class FIGI is expanded into venue-level listings.
- Primary listing is separated from additional/cross-listings.
- `VERIFIED` = independently confirmed by SEC for a US ticker/exchange.
- `CANDIDATE` = best global home-market/common-equity listing from symbology; official exchange confirmation is not yet available.
- No `null` values should appear in the evidence UI.
- OpenFIGI caching and API-key support remain enabled.
- Quote fields remain intentionally unavailable until a proper global quote provider is connected.

## Update on iPad

### GitHub Pages
Replace only:
- `index.html`

### Cloudflare Worker
Replace the current Worker code with:
- `worker/worker.js`

Then press **Deploy**.

You do **not** need to change or re-enter your existing `OPENFIGI_API_KEY` secret.

`wrangler.toml` is not needed when using the Cloudflare dashboard.

## Test

1. Open Worker `/health` and confirm `"version":"1.9"`.
2. Reload GitHub Pages and confirm `Build 1.9`.
3. Test Danaher first. Expected: DHR, CIK 313616, exchange should be recovered from SEC Submissions when available, and OpenFIGI should map from DHR.
4. Then test Krones, Toyota, Samsung Electronics, Alibaba and another Japanese/Hong Kong/Korean listing.

## Important limitation

OpenFIGI is global symbology, not an authoritative declaration of a company's primary exchange and not a live-price feed. Non-US `Primary listing` is therefore shown as `CANDIDATE` until corroborated by an official exchange/company filing source. This is deliberate.
