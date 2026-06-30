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
