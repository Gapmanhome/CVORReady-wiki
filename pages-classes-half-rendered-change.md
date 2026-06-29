---
type: class
status: open
instances: 1
sweep_done: false
---
# The Half-Rendered Change

**Pattern:** a rendered-document edit applied in one of the two PDF generators but not the other —
half-branded / half-fixed output.

## Instances
1. Branding work had to cover both the native PDFKit/AcroForm generator AND the Puppeteer/HTML
   generator (carrier bar, disclaimer, metadata Creator, HTML disclaimer, signing cert).

## Guard
Every rendered-document element -> covered in BOTH generators? (Note: the two generators also carry
DIFFERENT disclaimer wording — flag for consistency review, Tier 4.)
