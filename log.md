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
Applied the between-sessions efficiency recommendations as bookkeeping (no gate touched):
(1) Made `regulatory-knowledge.md` the canonical value store; value pages are now thin pointers
created lazily — slimmed the collision page accordingly. (2) `index.md` is now derived from page
front-matter rather than hand-typed. (3) Added `START-HERE.md` as the single session-orientation
read. (4) Added a live "what's owed" worklist (inside START-HERE). (5) Split lint into mechanical
(deterministic, run anytime) vs judgment (prompted) in `LINT.md`. One reconciliation flagged for
Gary: the index showed the collision threshold as ❓ while the ledger + value page record Brian's
✅ cert; the derived index now mirrors the record. Confirm that reflects Brian's actual attestation
before pushing. Nothing pushed — Gary gates the write.
