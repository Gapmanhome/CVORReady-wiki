# Maintenance

Bookkeeping the maintainer (model) owns. **You don't need to read this** unless an item is marked
**TOUCHES A VALUE** — those are the only ones that can affect what an auditor sees. Everything else
is filing: it keeps the repo tidy but changes nothing about compliance correctness.

## Open maintenance items
- **Staging Mirage sweep** — bug class hit 3 instances, sweep not yet run. Codebase quality
  (does a fix verified on staging actually hold in prod). Does **not** touch a certified value.
- **Collision page tidy** — `pages-values-collision-reporting-threshold.md` still restates sources
  instead of pointing to the ledger. Cosmetic; the value and status already match the ledger. Safe
  to leave.
- **Orphan templates** — the `_TEMPLATE` files aren't linked from `index.md`. Scaffolding. Harmless.

## Decisions for Gary (not the model's to make)
- **Flat vs folders** — docs describe `pages/values/` etc. as folders; the repo is actually flat
  (`pages-<area>-<name>.md`). Pick one and make the docs match. No correctness impact either way.
- **Missing `CLAUDE.md` / `RULES.md`** — referenced as the promotion targets throughout, but not
  present in the repo. Confirm whether they live elsewhere or still need creating.
- **Schema drafts unmerged** — `schema-PROPOSED-*` (CLAUDE.md §XI, WIKI.md §9) are cited as if live
  but aren't canon until Gary merges them.

## How this works
The model fixes filing silently and only surfaces an item here when it would change a value. If you
ever see **TOUCHES A VALUE** on a line, that one is worth a look. Otherwise this file runs itself.
EOF
echo "done"