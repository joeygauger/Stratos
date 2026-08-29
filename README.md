# Corporate Intelligence — Step 1.6 Entity Ranking & Type Detection

This build improves company search ranking without changing the already-working SEC/OpenFIGI Worker.

## Improvements
- Legal suffix normalization (Corporation/Corp/Inc/AG/GmbH/etc.)
- Exact canonical company names rank above broad partial matches
- Pension plans, retirement vehicles, master trusts, trusts, funds and finance/SPV entities receive ranking penalties unless the user explicitly searches for those terms
- Search results display a heuristic entity-type label:
  - Primary company candidate
  - Corporate entity candidate
  - Benefit / trust vehicle
  - Finance / SPV
  - Fund / foundation
  - Legal entity
- Shorter, cleaner names receive a slight preference for broad searches
- The UI explicitly marks these type labels as heuristic, not registry facts

## What to update
GitHub Pages only:
- index.html

You do NOT need to change Cloudflare.
You do NOT need to replace worker.js.
You do NOT need wrangler.toml.

Optional:
- README.md, if you want the repository documentation updated.

Expected Danaher behavior:
`DANAHER CORPORATION` should rank above Danaher retirement-plan / master-trust entities for a search of `Danaher`.
