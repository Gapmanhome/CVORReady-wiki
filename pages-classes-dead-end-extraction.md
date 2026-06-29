---
type: class
status: open
instances: 1
sweep_done: false
---
# The Dead-End Extraction

**Pattern:** a field is extracted and stored but has no path to be written — no confirm-card
field, no mapper case. It lives in the log and goes nowhere.

## Instances
1. MELT grant-date — extraction + mapper existed, no card path.

## Sweep (candidate — handoff §7.2)
Every extraction field -> does it have a complete extract -> confirm-card -> mapper -> DB-write path?
Sweep status: **not yet run**.

## Guard
Trace each extracted field end-to-end to a DB write before calling it "extracted."
