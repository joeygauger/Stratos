# Step 1.11 — Issuer Resolution

Architecture:
QUERY → GLEIF legal entities + OpenFIGI common-stock discovery → exclude product-like instruments → cluster listings into issuer families → infer home market → cross-match GLEIF legal, alternate and transliterated names → reject wrong-country/product-like legal entities → Security Master.

Key fixes:
- Multiple listings from one issuer are grouped before they reach Company Search.
- ETF/ETN/hedged/warrant/fund-like instruments are excluded from canonical issuer discovery.
- GLEIF alternate and transliterated names are used for issuer/legal-entity matching.
- Wrong-country legal-entity matches are rejected when the issuer family has a home-country signal.
- OpenFIGI discovery asks for Common Stock first, with broader equity fallback.
- Ambiguous results remain candidates instead of being silently promoted.

Regression targets:
Danaher → DHR / NYSE.
Krones → KRONES Aktiengesellschaft / German listing.
Toyota → Toyota Motor Corporation / 7203 / Japan, not ADRHEDGED.
Samsung → Samsung Electronics when supported by issuer/legal-entity evidence, not ETF/product-like Samsung instruments.

Update:
1. GitHub Pages: replace index.html.
2. Cloudflare Worker: replace worker/worker.js and Deploy.
3. Keep the existing OPENFIGI_API_KEY secret unchanged.

Health endpoint should show version 1.11 and issuerResolution=true.
