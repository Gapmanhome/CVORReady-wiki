---
type: regulatory-ledger
status: certified
certified_by: "Brian — verbal attestation via Gary (recorded per 2026-06-29 kickoff)"
basis: "each value cross-referenced against 3+ sources, primary each"
last_reviewed: "2026-07-01"
canonical_value_store: true
---
# Regulatory Knowledge — Certified Ledger

The CVORReady / ExeSketch regulatory values, as **certified by Brian** (verbal attestation via
Gary; each cross-referenced against 3+ sources, primary each). This is the record of what was
certified and what remains open — not an AI verdict. Values below are ✅ because Brian certified
them, logged as a verbal-via-Gary attestation per the standing convention.

> **This ledger is the canonical store for compliance values** — figure, sources, and Brian's cert
> record live here. Value pages under `pages/values/` are thin pointers that track page-local data
> (e.g. `used_by_forms`); on any conflict, this ledger wins. New value pages are created **lazily**,
> only when a form references the value — so the absence of a page for a certified value is by
> design, not drift. The derived `index.md` mirrors this ledger for value status.

---

## CERTIFIED VALUES (✅)

### Highway Traffic Act
- **Collision reporting threshold — $5,000.** ✅
  Cite: **HTA s.199(1)**, effective Jan 1 2025. No separate CVOR threshold — it tracks s.199.
  State as **"$5,000 combined damage, or any personal injury."**  *(Replaces $2,000.)*

### Hours of Service — O. Reg. 555/06
- **Cycle resets — 36 / 72 hours.** ✅  Cite: **O. Reg. 555/06 s.14.**

### Cargo Securement — NSC Standard 10 (via O. Reg. 363/04)
- **NSC Standard 10 = Cargo Securement.** ✅  (The 14 → 10 correction was right.)
- **Load-check timing.** ✅  Cite: **NSC Standard 10 s.3** via O. Reg. 363/04.
  - **First check:** before driving **and** within **80 km**.
  - **Recurring re-check:** earliest of **duty-status change / 3 hrs / 240 km**.
  - **Exemption:** load sealed or inaccessible.

### Critical Injury — OHSA s.51 / O. Reg. 420/21
- **Reporting.** ✅  Notify **immediately** + **written report within 48 hrs**.
- **On-highway MVC carve-out (s.2(2)).** Disapplies the OHSA notice **and** written report for a
  worker hurt in an on-highway collision — **unless** working at a project, or not in the vehicle.
  The carve-out removes the **OHSA obligation only**: HTA/CVOR collision reporting and **WSIB
  (Form 7, within 3 business days)** still apply.

### MELT (Mandatory Entry-Level Training)
- **Three states: Exempt / Required / Verify.** ✅
  - **Verify** is the default on any ambiguity.
  - **Manual confirmation is authoritative** and is recorded.
  - Read the **Class A class-change date from licence history** — *not* "date first licensed."

### Commercial-driver medical-exam interval — age-banded ✅ (certified 2026-07-01)
Brian-certified via Gary; pressure-tested against live code (2026-07-01). Commercial Class A–F,
**age-banded** (not a single interval):
  - **Under 46 → every 5 years (1825 d).**
  - **46–64 → every 3 years (1095 d).**
  - **65+ → every 1 year (365 d).**
  Cite: **MTO / CCMTA national medical standard** (Gary: default to MTO; O. Reg. 340/94 not pinned).
  Condition-specific MTO reviews can shorten any band — case-by-case, not the base schedule.
  > ⚠️ **Implementation defect (open, not a value question):** live code contradicts this cert in
  > two places — `carrierready-content.ts:107` prints "every 2 years (730 days)" for 46–64 in an
  > **auditor-facing document** (URGENT), and `scoring.ts:56` returns 730 in the (currently dead)
  > interval function. The *value* is certified here; the *code* must be corrected to match. Tracked
  > in `security-round2-scorecard.md`.

---

## OPEN — NOT in the certified set (carry as ❓; confirm before treating as done)

Per the "flagged ≠ done" lesson, none are assumed resolved.

- **HOS log-audit interval.** ❓
- **O. Reg. 638A mentorship requirement.** ❓
- **30-day accident-preventability window.** ❓
- **Document-retention conventions.** ❓
- **Ontario HOS set-fine figure.** ❓
- **`$19,277`** (removed bad string, RULES Domain E) — correct replacement value / disposition
  unknown. ❓

---

## Provenance & convention
- **Certification:** Brian, verbal, via Gary. Logged as a verbal-via-Gary attestation
  (who / when / what), **not** as a marked document — per the standing rule that editorial /
  certification markers must never live in rendered content.
- **Single shared DB:** ExeSketch dev = prod (one `DATABASE_URL`); any content edit is live to
  clients immediately. Both PDF generators (Puppeteer/Handlebars + PDFKit/AcroForm) render from
  the same `carrierready_templates.content` column — fix the DB content, prove both renders.
  > ⚠️ **Discrepancy flagged 2026-07-01:** the Replit pass found only ONE generator (PDFKit); no
  > Puppeteer generator located. Either it was removed (this note + the Half-Rendered Change class
  > are stale) or the agent missed it. Confirm before relying on the two-generator assumption.
