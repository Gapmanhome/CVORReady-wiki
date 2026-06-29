---
type: class
status: open
instances: 3
sweep_done: true
---
# The Orphaned Override

**Pattern:** a capability added via shared middleware/helper that some files don't inherit
because they predate it or are mounted separately.

## Instances
1. Admin-view override missing — import path
2. Admin-view override missing — storage path
3. Admin-view override missing — abstract path

## Sweep
Hit reactively 3x before one sweep mapped all ~105 routes and found the remaining 9 (4
compliance-documents.ts + 4 integrations.ts + 1 platform.ts). Fixed via shared
`resolveFleetContext`. Sweep status: **done** — 95 ADMIN-OK, 9 were ADMIN-MISSING.

## Guard
Every router file: does it inherit the admin-view middleware, or call getFleetForUser directly?
