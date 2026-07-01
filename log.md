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
