---
type: regulatory-ledger
status: certified
certified_by: "Brian — verbal attestation via Gary (recorded per 2026-06-29 kickoff)"
basis: "each value cross-referenced against 3+ sources, primary each"
last_reviewed: "2026-07-01"
canonical_value_store: true
---
# Regulatory Knowledge — Certified Ledger

The certified regulatory values. This ledger is the canonical store — figure, sources, cert record.
Each value is now tagged with **which product / surface it lives in**, because CVORReady and
ExeSketch are SEPARATE products (see Architecture below). On any conflict, this ledger wins.

---

## CERTIFIED VALUES (✅)

### Collision reporting threshold — $5,000
Cite: **HTA s.199(1)** (eff. Jan 1 2025). "$5,000 combined damage, or any personal injury."
*(Replaces $2,000.)* Not yet code-audited for stray variants — see open work.

### HOS cycle resets — 36 / 72 hours
Cite: **O. Reg. 555/06 s.14.** Not yet code-audited.

### Cargo securement (NSC Standard 10 via O. Reg. 363/04)
- First check: **within 80 km** of trip start.
- Re-check at earliest of **duty-status change / 3 hrs / 240 km**.
- Exempt if sealed/inaccessible.
- **CVORReady:** scenario line corrected 2026-07-01 (250 km → 240 km). Main cargo doc already correct.
- **ExeSketch:** clean (cargo rows fixed in prior sessions; re-verified clean 2026-07-01).

### Critical injury (OHSA s.51 / O. Reg. 420/21)
Notify immediately + written report within 48 hrs. On-highway MVC carve-out (s.2(2)) removes the
OHSA obligation only; HTA/CVOR reporting + WSIB (Form 7, 3 business days) still apply. Not yet code-audited.

### MELT — three states (Exempt / Required / Verify)
Verify is default. Manual confirmation authoritative. Read Class A change date from licence history.
Not yet code-audited.

### Commercial-driver medical-exam interval — age-banded ✅ (certified 2026-07-01)
Brian-certified via Gary; sourced against 3 official refs (ontario.ca commercial-driver standard,
MTO Truck Handbook, mto.gov.on.ca / CCMTA). Commercial Class A–F:
- **Under 46 → 5 years (1825 d)** · **46–64 → 3 years (1095 d)** · **65+ → 1 year (365 d)**
- Cite: **O. Reg. 340/94 (Drivers' Licences) + CCMTA Medical Standards.** (NOT "O. Reg. 339/05" =
  Demerit Points; NOT "NSC Std 6 Schedule 1" — both were wrong citations found in code and removed.)
- Boundary: age 46 sits in the 3-yr band. Condition-specific MTO reviews can shorten any band.
- **CVORReady:** CORRECTED 2026-07-01 across **9 locations** — DQ form (both sections), 2 scenario
  lines, detail text, exam question, 2 email lines, email comment, phase5 script. All read 5/3/1
  with O. Reg. 340/94. Verified accurate by the scoring oracle (37/37, see scorecard).
- **ExeSketch:** no age-banded medical-renewal content present (confirmed clean 2026-07-01).
- ⚠️ **Root-cause note:** the CVORReady errors were US/FMCSA values (24-mo card / "2yr→annual→6mo")
  dropped into Ontario age-banded fields. This conflation pattern is why the OTHER certified values
  above still need a code audit — Brian's number being right does not prove the code carries it.

---

## OPEN — NOT certified (carry as ❓)
- HOS log-audit interval · O. Reg. 638A mentorship · 30-day accident-preventability window ·
  document-retention conventions · Ontario HOS set-fine · **$19,277** replacement (unknown).

---

## ARCHITECTURE — two separate products (corrected 2026-07-01)
The single most important correction this session. The old wiki blended these into one model
("single shared DB / two generators / live to clients") and that blend caused repeated confusion.
They are separate products with separate architecture:

- **CVORReady (cvorready.ca)** — the platform: scoring engine, driver-qual forms, UI, notifications.
  Renders documents **from source at generation time. ONE generator. NO live content DB.** A wrong
  source value reaches a client only when a document is generated. Files: `scoring.ts`,
  `carrierready-content.ts`, `library-scenarios.ts`, `exam-questions.ts`, `orchestrator.ts`.
- **ExeSketch (exesketch.com)** — generates the compliance documents, nothing else. **Live content
  DB** (`carrierready_templates.content`), **TWO generators** (G1 Puppeteer/Handlebars + G2
  PDFKit/AcroForm), content live to clients at generation. INSERT ... ON CONFLICT DO NOTHING (re-seed
  never overwrites existing rows).

> **Rule going forward:** every prompt names its target product. Same document codes exist in both
> (e.g. CR-DQ-004 = a medical form in CVORReady, an Annual Abstract Review Record in ExeSketch) —
> a prompt run against the wrong product returns "clean" and looks done. Do not trust architecture
> claims from memory; the codebase is truth for architecture, this ledger is truth for values.

## Certification convention
Values are ✅ only when Brian certifies via Gary (verbal attestation, logged who/when/what).
The model never marks ✅ itself. Gary does every push.
