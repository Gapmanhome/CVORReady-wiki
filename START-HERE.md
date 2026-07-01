# Start here

Read this first. Two products, the certified values, and the one gate.

## FIRST: two separate products (do not blend them)
- **CVORReady (cvorready.ca)** — the platform: scoring, forms, UI, notifications. Renders from
  SOURCE at generation time. ONE generator. NO live content DB.
- **ExeSketch (exesketch.com)** — generates the compliance documents only. LIVE content DB, TWO
  generators, content live at generation.

Same document codes exist in both with different meanings. **Every task/prompt must name its
target product** — a prompt run against the wrong one returns "clean" and looks done.

## 1. What's settled (certified by Brian — trust these)
- **Collision threshold — $5,000** (combined damage, or any injury). *code-audit pending*
- **HOS cycle resets — 36 / 72 hours.** *code-audit pending*
- **Cargo securement (NSC Std 10) — 80 km first / 240 km / 3 hrs / duty-change.** CVORReady fixed; ExeSketch clean.
- **Critical-injury reporting** (OHSA: immediate + 48-hr written; MVC carve-out). *code-audit pending*
- **MELT — three states** (Verify is default). *code-audit pending*
- **Medical-exam interval — age-banded** (Class A–F): under 46 → 5 yr · 46–64 → 3 yr · 65+ → 1 yr.
  Cite **O. Reg. 340/94 + CCMTA**. CVORReady CORRECTED across 9 locations 2026-07-01; scoring verified.

Full detail + sources: `regulatory-knowledge.md` (values now tagged by product).

## 2. What's NOT settled (confirm before use)
- Awaiting Brian: HOS log-audit interval · O. Reg. 638A mentorship · 30-day preventability window ·
  document-retention · Ontario HOS set-fine. · **$19,277** replacement unknown.
- **Code-audit gap:** only the medical value has been audited in code. The other 5 certified values
  are trusted from Brian's number but NOT yet checked in the codebase for stray/US-framework variants.

## Product / security status
- Scoring engine (CVORReady): **verified accurate** — 37/37 oracle vs documented rules, ESM test bug
  fixed 2026-07-01. See `security-round2-scorecard.md`.
- Round 2 OWASP/BOLA: see scorecard. Domain A (tenant isolation) verified on STAGING write-paths only
  — prod + read-path still outstanding.

## The one gate
A value is settled only when Brian certifies it, through Gary. The model never marks ✅ itself.
Gary does every push, batched at end of session. A wrong value reaching an auditor is the one
failure that can't be undone.

---
*Filing/process detail: `MAINTENANCE.md`. You don't need it unless a line is flagged as touching a value.*
