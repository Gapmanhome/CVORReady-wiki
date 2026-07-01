---
type: security-scorecard
program: "OWASP API Security Top 10 (2023), BOLA-weighted — Round 2"
last_verified: "2026-07-01 (Replit read-only pass)"
rule: "enumerate, never assert — every status backed by file:line + environment"
---
# Round 2 OWASP/BOLA — reconciled scorecard

Status as of the **2026-07-01 Replit verification pass**. This supersedes any earlier prose summary.
Where the pass and a prior claim disagreed, the **evidence wins** and the item is marked down.
Governing rule: *enumerate, never assert*; every "verified" carries file:line + which environment.

## Launch read
Tenant isolation (Domain A) — the gate — is **verified on staging for write-paths only**. That is
strong but NOT the "shut, prod-guarded" gate a prior summary implied. Two honest gaps: prod
(heliumdb) not re-verified, and read-path (SELECT) leakage not covered. Treat A as *substantially
verified, prod + read-path re-confirm outstanding.*

## Per-domain status

| Domain | Status | Evidence (file:line) | Env |
|---|---|---|---|
| **A — Tenant isolation (write)** | ✅ verified | `isolation.test.ts` — 18/18 pass, 9 write routes, cross-fleet negative + own-fleet positive | **staging (Neon)** |
| A — prod + read-path | ❌ outstanding | prod (heliumdb) not re-run; SELECT-path leakage not covered by the suite; "50/50 adversarial" not run this pass | — |
| **B — Auth/session** | 🟡 mostly | managed-carrier guard `managed-carrier-guard.ts:18-22` @ `platform.ts:61`; no priv-esc path found | source |
| B — invite role-cap | ❓ cannot-confirm | `/team/join/:token` handler not locatable this pass — read the handler body | source |
| **C — Scoring oracle** | ❌ broken | `scoring-medical.test.ts` fails to execute (`require` in ESM `"type":"module"`); no interval assertion; no grade-band / empty-fleet / conviction-cap cases | dev |
| **D — Grade LETTER** | ✅ verified | API-sourced on all live report surfaces; local fns 5-band match `scoring.ts:323-328` | source |
| D — Grade COLOR | 🟡 diverges (cosmetic) | `shared-report.tsx:87`, `reports.tsx:314`, `reports-insurance.tsx:168`, `reports-monthly.tsx:174` — 3-band color; D renders same red as F | source |
| **E1 — Structural** | ❌ stale / unconfirmed | phantom codes CR-CS-001/004 **still present** `carrierready-content.ts:1314/1388`, `admin.ts:3699`; `{{DEPOT_ADDRESS}}` + Section-5-in-PDF need a generated doc to confirm | source |
| **E2 — Branding image** | ✅ clean | `nextgen-logo.png` is an **orphan** (0 code refs); embedded in no PDF path → **delete it** | dev |
| **E3 — Content correctness** | ✅ closed | Brian's certified ledger IS E3 | — |
| **F — Data lifecycle** | ❌ deferred | forward-looking; matters once real clients exist | — |
| **G — Cost/resilience** | ❌ deferred | forward-looking | — |
| **Gitleaks** | ❓ cannot-confirm | binary wouldn't install; manual partial scan 0 hits / 359 commits — not equivalent to gitleaks | git |

## Open fix items (proposed by the pass — NOT applied; Gary disposes)

1. ⚠️ **URGENT — `carrierready-content.ts:107`**: "every 2 years (730 days)" → "every 3 years (1,095 days)".
   The only wrong value on a **live, auditor-facing** surface. TOUCHES A VALUE.
2. **`scoring.ts:56`**: 730 → 1095, fix the "Biennial" comment. Dead function today, but fix before it's wired.
3. **Delete `assets/nextgen-logo.png`** — orphan binary, accidental-embed risk.
4. **Repair `scoring-medical.test.ts`** (ESM import) so Domain C can run; add the interval assertion + boundary cases.
5. **Re-verify Domain A on prod + read-path**; run the 50/50 adversarial to restore the full gate claim.
6. **Read `/team/join/:token`** to confirm role comes from the invite record, not user input.
7. **Confirm the generator question** — one (PDFKit) or two (Puppeteer too)? Resolves whether the
   Half-Rendered Change class and the ledger's two-generator note are stale.
8. **Run real gitleaks** (full history) when network allows.

## Note — `scoring.ts:99` (not a regulatory value)
A separate `730` at `scoring.ts:99` is a UX warning→overdue threshold for abstract/annual-review
age. No standard cited; it *does* affect pillar score. Not a compliance value — flag for design review,
don't "fix" it to 1095.
EOF
echo "scorecard created"