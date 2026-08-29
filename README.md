# Step 1.10 — Parallel Global Discovery

Core architecture change:
Company Search now performs legal-entity discovery (GLEIF) and listed-issuer discovery (OpenFIGI) in parallel, merges the candidate sets, and only then resolves the canonical company.

Why:
A broad brand/company query such as Toyota, Samsung or Krones can return many subsidiaries in GLEIF before the listed parent. GLEIF remains the legal-identity authority, but no longer acts as the only discovery source.

Flow:
QUERY
→ GLEIF legal-entity candidates
→ OpenFIGI listed-issuer candidates
→ merged ranking
→ selected listed issuer
→ targeted GLEIF legal-entity verification
→ Security Master / primary listing / additional listings

Additional fixes:
- German "Aktiengesellschaft" is normalized as a legal suffix.
- Betriebskrankenkasse / Krankenkasse receive a strong ranking penalty for broad company searches.
- A discovered market ticker can be passed into market resolution so non-US issuers no longer depend only on company-name search.
- Build and backend health version are synchronized at 1.10.

Files to replace:
1. GitHub Pages: index.html
2. Cloudflare Worker: worker/worker.js, then Deploy

Existing OPENFIGI_API_KEY secret remains unchanged.
