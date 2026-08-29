# Corporate Intelligence — Step 1.4 Market Identity

## What changed
This version separates legal identity (GLEIF) from market identity (SEC/OpenFIGI).

Resolved market fields when evidence is strong enough:
- Public status
- Ticker
- Exchange
- CIK (US)
- FIGI
- Market confidence
- Evidence reason

Important: failure to find a public listing is shown as UNRESOLVED, not PRIVATE. A reliable PRIVATE classification needs affirmative company-registry / ownership evidence.

## Architecture
GitHub Pages = frontend/PWA.
Cloudflare Worker = small API bridge for SEC and OpenFIGI.
GLEIF remains browser-side for legal entity search.

## Deploy the Worker from iPad
1. Create a free Cloudflare account.
2. Go to Workers & Pages -> Create -> Worker.
3. Replace the default Worker code with worker/worker.js from this package.
4. Deploy.
5. Copy the workers.dev URL.
6. Open the Corporate Intelligence app, paste the URL under MARKET DATA BRIDGE and press Connect.

Optional:
Create an OpenFIGI API key and save it in the Worker as secret OPENFIGI_API_KEY. The app also works without it at OpenFIGI's lower anonymous rate limit.

## GitHub Pages update
Upload/replace index.html, sw.js, manifest.webmanifest and the two icons in your current GitHub Pages repository. Keep the worker folder out of the Pages root if preferred; it is deployment source code only.
