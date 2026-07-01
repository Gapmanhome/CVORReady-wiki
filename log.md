# Log

Append-only. One entry per ingest / query / lint. Prefix `## [YYYY-MM-DD] <kind> | <title>`.

## [2026-06-29] scaffold | Repo initialized
Stood up the learning-loop wiki skeleton: page taxonomy (values/classes/prompts/domains/staging),
index + log, canon/staging rule, autonomy boundary, prompted adversarial lint. Seeded the four
codebase-earned bug classes and one example value page (collision threshold, ❓ pending Brian).
Schema edits for CLAUDE.md (iteration ritual) and WIKI.md (wiki shape) drafted in schema/ for
Gary to review/merge. Not yet pushed — awaiting Gary's gate.

## [2026-06-29] remote | Configured origin
Added remote origin -> https://github.com/Gapmanhome/CVORReady-wiki.git, branch main.
Added PUSH.md. Repo is ready for Gary to push (model has no GitHub credentials; push is Gary's).

## [2026-06-30] restructure | Efficiency pass — 5 changes (proposed, awaiting Gary's push)
Made regulatory-knowledge.md the canonical value store; value pages now thin pointers; index.md
derived from front-matter; added START-HERE.md + LINT.md; split lint mechanical vs judgment.
Collision threshold reconciled to ✅ in the index to match the ledger + value-page record.

## [2026-06-30] cleanup | Fixed duplicate + flat-name links
Mechanical lint against the live tree caught a duplicate collision page (slimmed copy had landed
without the pages-values- prefix). Removed the stray; index links corrected to the flat filenames.

## [2026-06-30] refocus | Split human view from maintenance
START-HERE.md cut to two things only: certified values + unconfirmed values + the one gate.
Moved all filing/bookkeeping/structural decisions to MAINTENANCE.md, which the human ignores
unless a line is tagged TOUCHES A VALUE. Reduces process noise without touching any gate.

## [2026-07-01] verify | Replit pass reconciled — medical interval promoted + Round 2 scorecard
Replit read-only audit returned. Medical-exam interval pressure-tested: regulation confirms Brian
(age-banded 1825/1095/365) — PROMOTED to ledger as ✅. Code diverges in two places (scoring.ts:56
dead fn; carrierready-content.ts:107 auditor-facing doc text = "2 years/730 d" — URGENT fix, TOUCHES
A VALUE). Round 2 status captured in new security-round2-scorecard.md, evidence-backed: Domain A
verified on STAGING write-paths only (prod/read-path outstanding); Domain C oracle test broken (ESM);
E1 phantom codes still present; E2 logo is orphan (not embedded) — delete; gitleaks still not truly
run. Discrepancy flagged: only one PDF generator (PDFKit) found — Half-Rendered Change class premise
under review. Staging medical-interval candidate promoted → delete. Nothing pushed; Gary gates.

## [2026-07-01] certify | Medical-exam interval — Brian confirmed with sources
Brian confirmed the age-banded schedule (1825/1095/365) against 3 official sources (ontario.ca
commercial-driver standard, MTO Truck Handbook, mto.gov.on.ca / CCMTA). Ledger cite strengthened
with the sourced basis + the age-46 boundary. Value fully certified. Remaining: apply the code
correction (content.ts:107 auditor-facing + scoring.ts:56) via the CVORReady Replit prompt — the
live product still ships 730 until that runs.

## [2026-07-01] fix | Medical-interval sweep — CVORReady, 9 locations
Full enumerate-diagnostic found the interval wrong in 9 CVORReady locations (DQ form both sections,
2 scenarios, detail text, exam question, 2 emails, email comment, phase5 script) — all US/FMCSA
values ("2yr→annual→6mo", 12/24-month card) dropped into Ontario age-banded fields, plus 2 wrong
citations (339/05, NSC Std 6). All corrected to 5/3/1 (1825/1095/365) with O. Reg. 340/94 + CCMTA.
Cargo scenario line fixed (250→240). Sourced against 3 official refs; Brian confirmed. Not deployed.

## [2026-07-01] verify | Scoring engine accuracy — CVORReady
ESM test bug fixed (require→dynamic import; static import would hoist before Date-freeze). Built an
oracle with expected values hand-derived from documented rules (not engine output). 37/37 pass:
grade boundaries, empty fleet (=58, no crash), conviction cap (=36), age intervals (1825/1095/365),
expiry warn/overdue windows. Engine is accurate per its rules. Caveats: tests math given correct
inputs, not input fidelity; `ageAdjustedMedicalIntervalDays` is a private fn nothing calls (confirm
wiring). Regression test now exists.

## [2026-07-01] correct | Architecture — CVORReady and ExeSketch are SEPARATE products
Root cause of this session's confusion: the wiki blended two products into one architecture model.
CVORReady (cvorready.ca) = platform, renders from source, 1 generator, no live content DB. ExeSketch
(exesketch.com) = generates compliance docs, live content DB (carrierready_templates.content), 2
generators (Puppeteer + PDFKit). Same doc codes, different meanings across the two. ExeSketch pass
confirmed it clean on both cargo + medical. All architecture claims now product-tagged; the old
"single shared DB / two generators / live immediately" note was ExeSketch-only, wrongly applied to
CVORReady. Half-Rendered-Change class rescoped to ExeSketch. Rule added: every prompt names its product.

## [2026-07-01] close | Session write-back (batched, one diff)
Changed: regulatory-knowledge.md (values tagged by product + medical fix recorded), START-HERE.md
(product distinction + code-audit gap), security-round2-scorecard.md (Domain C verified), index.md,
log.md. Delete pages-staging-medical-exam-interval.md (promoted). Open: code-audit the other 5
certified values (US/Ontario conflation risk); Domain A prod+read-path; confirm dead interval fn
wiring; Geotab integration is net-new (SDK Add-In/data connector, not yet built).
