# CVORReady Knowledge Wiki

The learning loop (handoff §7) as a persistent, interlinked, LLM-maintained knowledge base.
Its one job: **every iteration writes what it learned back here, so the next iteration inherits
it instead of re-deriving it.** Knowledge compounds in the repo, not in any model's memory.

## Why a repo (and not "the model remembers")
A model does not carry state across sessions. Persistence has to live somewhere Gary owns, with
a load-it-back step at the top of each session — otherwise you can't tell when it goes stale.
This repo is that store. The model maintains it *during* a session; the repo is the continuity
*between* them.

## The iteration ritual (the mechanism that keeps it fresh)
- **Start:** load this wiki (pull from GitHub when reachable, or upload the files). Read the
  pages relevant to the task before doing anything.
- **During:** the model updates pages, cross-refs, `index.md`, and `log.md` as work proceeds.
- **End:** the model hands back the changed pages as a diff. **Gary commits and pushes.** The
  model never publishes — Gary gates the write.

## Layers
1. **Raw sources** (immutable) — verified, agreed regulatory + project sources. Read, never edited.
2. **Wiki pages** (`pages/`) — model-owned summaries/entities/concepts, fully cross-referenced.
3. **Schema** — `CLAUDE.md` gains the iteration ritual; `WIKI.md` carries the wiki's shape.
   Drafts of both edits are in `schema/` for Gary to review and merge (not auto-applied).

## Canon rule (what may enter)
Only **verified knowledge + agreed sources**. Every regulatory value carries **both** a primary
source (statute / O.Reg / HTA) and confirmed secondary corroboration; on conflict, primary and
statute win (RULES §10). Anything unverified lives in `pages/staging/` flagged "not yet canon"
and never silently becomes fact.

## Autonomy boundary
- Model **auto-owns bookkeeping only**: drafting/updating pages, cross-refs, index/log, flagging
  contradictions.
- **Gary is the single required contact for every decision.**
- Compliance values stay **❓** until **Brian** certifies — and that reaches the wiki *through
  Gary*. The model never contacts Brian and never writes ✅/❌ on its own.
- **Promoting** a lesson INTO `CLAUDE.md`/`RULES.md` (tightening the bar) is **Gary-only** — per
  the RQGM note, that act stays human or the loop blesses its own standard.

## Lint (anti-staleness — prompted, not automatic)
When Gary triggers it, the lint pass runs *adversarially against the maintainer's own drift*:
claims a newer iteration superseded, values that crept off the certified set, orphan pages,
missing cross-refs. Lint **proposes**; Gary/Brian dispose.

## Files
- `index.md` — content catalog (read first on query).
- `log.md` — append-only timeline (`grep "^## \[" log.md | tail -5`).
- `pages/values|classes|prompts|domains|staging/` — the page types (see `_TEMPLATE.md` in each).
