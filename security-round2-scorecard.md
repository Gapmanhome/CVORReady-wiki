---
type: security-scorecard
program: "OWASP API Security Top 10 (2023), BOLA-weighted — Round 2"
last_verified: "2026-07-01"
rule: "enumerate, never assert — every status backed by file:line + environment"
---
# Round 2 OWASP/BOLA — reconciled scorecard

Status as of 2026-07-01. Evidence wins over prior prose summaries. Every "verified" carries
file:line + environment. **Scope: CVORReady (cvorready.ca)** unless noted.

## Launch read
Tenant isolation (Domain A) — the gate — is verified on **staging, write-paths only**. Strong but
NOT a shut, prod-guarded gate. Prod (heliumdb) + read-path (SELECT) leakage still outstanding.

## Per-domain status

| Domain | Status | Evidence | Env |
|---|---|---|---|
| **A — Tenant isolation (write)** | ✅ verified | `isolation.test.ts` 18/18, 9 write routes, cross-fleet neg + own-fleet pos | staging (Neon) |
| A — prod + read-path | ❌ outstanding | prod not re-run; SELECT-path not covered; 50/50 adversarial not re-run | — |
| **B — Auth/session** | 🟡 mostly | managed-carrier guard `managed-carrier-guard.ts:18-22` @ `platform.ts:61`; no priv-esc found | source |
| B — invite role-cap | ❓ cannot-confirm | `/team/join/:token` handler not located this pass | source |
| **C — Scoring engine** | ✅ **VERIFIED 2026-07-01** | ESM test bug FIXED (`require`→dynamic import); oracle 37/37 pass, expected values hand-derived from documented rules (grade bands, pillar weights, conviction cap, medical intervals, empty/worst-case). Regression test now exists. | dev, frozen clock, no DB |
| **D — Grade LETTER** | ✅ verified | API-sourced all live surfaces; 5-band match `scoring.ts:324-328` | source |
| D — Grade COLOR | 🟡 diverges (cosmetic) | 4 report pages 3-band color; D renders same red as F | source |
| **E1 — Structural** | ❌ stale | phantom codes CR-CS-001/004 still present; DEPOT_ADDRESS + Section-5 need a generated doc | source |
| **E2 — Branding image** | ✅ clean | `nextgen-logo.png` orphan (0 refs) → delete | dev |
| **E3 — Content correctness** | 🟡 partial | Medical value fully corrected + verified. **Other 5 certified values NOT yet code-audited** — the US/Ontario conflation pattern means this is real risk, not bookkeeping. | — |
| **F — Data lifecycle** | ❌ deferred | needed for real clients + Geotab partner terms (privacy, breach 24-72h, data handling) | — |
| **G — Cost/resilience** | ❌ deferred | per-document LLM cost at scale | — |
| **Gitleaks** | ❓ cannot-confirm | binary wouldn't install; manual partial 0/359 commits — not equivalent | git |

## Scoring verification detail (Domain C — closed this session)
- ESM bug: `require()` in a `"type":"module"` package → converted to dynamic `await import()`
  (static import would hoist before the Date-freeze). Test now executes.
- `ageAdjustedMedicalIntervalDays` had `export` added (visibility only, zero logic) to be testable.
  NOTE: it is a **private function nothing calls today** — correct + tested, but confirm it gets
  wired in wherever future "next renewal due" logic should use it. A correct uncalled fn does nothing.
- Oracle proved the engine computes what the rules say (grade boundaries flip correctly; empty fleet
  = 58, no crash; conviction penalty caps at 36; intervals return 1825/1095/365; expiry warn/overdue
  fire at right days). This tests the MATH given correct inputs — it does NOT test that the app feeds
  correct inputs (real medical dates, conviction counts). Input-fidelity is a separate later check.
- Boundary quirk (not a fail): `/365.25` divisor keeps a driver in the younger band ~1 day past the
  exact birthday. No rule specifies the divisor — flag for Brian if the 1-day edge matters.

## Open fix items (proposed — Gary disposes)
1. **Re-verify Domain A on prod + read-path**; re-run 50/50 adversarial to restore the full gate.
2. **Code-audit the other 5 certified values** (collision, HOS, cargo, critical-injury, MELT) for
   stray/US-framework variants — same enumerate-diagnostic used for medical. Highest compliance lever.
3. Repair/keep the scoring regression test in CI so the medical fix can't drift.
4. Confirm the dead `ageAdjustedMedicalIntervalDays` is wired where intended.
5. E1 phantom codes; delete orphan `nextgen-logo.png`; grade-color 5-band; real gitleaks.
6. Data-governance layer (F) for client-facing + Geotab partner obligations.
