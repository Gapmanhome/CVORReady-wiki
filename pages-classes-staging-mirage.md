---
type: class
status: open
instances: 3
sweep_done: false
---
# The Staging Mirage

**Pattern:** a fix "proven" on staging/Neon behaves differently in production/heliumdb — usually
env or binary-packaging differences.

## Instances
1-3. pdftoppm / poppler-utils packaging — fooled verification 3x this session.

## Guard
ALWAYS confirm WHICH DB / WHICH env a verification landed in. USE_STAGING_DB=true is dev-env only;
prod cvorready.ca -> heliumdb. Confirm a dependency resolves in PROD, not just dev.
