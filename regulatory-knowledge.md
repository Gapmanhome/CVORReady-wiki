---
type: regulatory-ledger
status: certified
certified_by: "Brian — verbal attestation via Gary (recorded per 2026-06-29 kickoff)"
basis: "each value cross-referenced against 3+ sources, primary each"
last_reviewed: "2026-06-29"
---
# Regulatory Knowledge — Certified Ledger

The CVORReady / ExeSketch regulatory values, as **certified by Brian** (verbal attestation via
Gary; each cross-referenced against 3+ sources, primary each). This is the record of what was
certified and what remains open — not an AI verdict. Values below are ✅ because Brian certified
them, logged as a verbal-via-Gary attestation per the standing convention.

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

---

## OPEN — NOT in the certified set (carry as ❓; confirm before treating as done)

These were enumerated previously (WIKI §7 / prior cert-list draft) but do **not** appear in the
2026-06-29 certified summary. Per the "flagged ≠ done" lesson, none are assumed resolved.

- **Medical-exam interval — 730 d (system) vs MTO 1095 d.** ❓ Highest-priority gap: previously
  flagged as a likely **contradiction**, and it touches the **scoring engine's** medical-interval
  logic. If contradicted, this is HIGH severity (RULES §4). Confirm whether certified elsewhere.
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
