# Corporate Intelligence — Step 1.3
Expanded entity resolution build:
- Live GLEIF legal entity search
- Match confidence and country filtering
- GLEIF declared parent/child relationship resolution
- Registered-office vs headquarters conflict detection
- Stable Canonical Company ID
- Source provenance architecture
- Saved canonical company records on-device

OpenFIGI and SEC are designed as the next market-identity enrichment. OpenFIGI supports ISIN/ticker/FIGI mapping; SEC publishes ticker/CIK/exchange association datasets. A backend/serverless layer is recommended before relying on these browser-side.
