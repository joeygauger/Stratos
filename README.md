# Corporate Intelligence — Step 1.4.1 Connection Fix

This build fixes the iPad/Safari Market Data Bridge connection check.

Changes:
- The confirmed Cloudflare Worker URL is preconfigured.
- Worker URLs are normalized correctly (with or without a trailing slash).
- Health check uses explicit CORS, no-store caching and a 10-second timeout.
- The app validates the actual health payload, not merely any HTTP response.
- Detailed connection errors are displayed in the UI.
- Market-resolution calls also use no-store and show HTTP/API errors.
- Service-worker cache bumped so GitHub Pages does not keep the old frontend.

Expected health response:
{"ok":true,"service":"Corporate Intelligence Market Identity"}

After deployment to GitHub Pages, the Market Data Bridge should auto-test on page load and show:
Connected ✓ Market Identity is live.

Cloudflare itself does not need to be changed for this build.
