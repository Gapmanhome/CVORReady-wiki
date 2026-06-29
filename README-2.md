# CVORReady Knowledge Wiki

The learning loop (handoff §7) as a persistent, interlinked, LLM-maintained knowledge base.
Its one job: **every iteration writes what it learned back here, so the next iteration inherits
it instead of re-deriving it.** Knowledge compounds in the repo, not in any model's memory.

## Why a repo (and not "the model remembers")
A model does not carry state across sessions. Persistence has to live somewhere Gary owns, with
a load-it-back step at the top of each session — otherwise you can't tell when it goes stale.
This repo is that store. The model maintains it *during* a session; the repo is the continuity
*between* them.

## The iteration ritual
- **Start:** load this wiki and read the pages relevant to the task before doing anything.
- **During:** work the task. Notice what's reusable — don't stop to document everything.
- **End:** write back the **minimum useful trace as ONE diff** (rule below). Gary commits and
  pushes. The model never publishes — Gary gates the write.

## Minimum write-back — the daily rule
A live loop, not paperwork. Each session leaves the smallest useful trace, not an update to
every page.
- **Floor (always):** one `log.md` line. A single append, near-zero cost — the trace that proves
  the loop ran.
- **Only if it actually changed:** a value page (a value moved), a class page (a bug recurred),
  a prompt page (a genuinely reusable shape emerged — most sessions: none), a staging note.
- **`index.md`:** only when a page is added or removed — not on every edit.
- **Never manufacture edits to look diligent.** Padding buries the one signal that mattered
  under churn someone then has to review.
- **One diff, not scattered files.** Batch the whole session's write-back into a single thing to
  review and upload.
- **Lint** stays prompted-only (below). Don't turn pruning into a chore.

## What does NOT get simpler
The compliance-authority controls stay strict because the domain is: primary + secondary source
on every value, ❓ until Brian certifies (via Gary), Gary-only promotion into CLAUDE.md/RULES,
canon vs staging. A wrong value reaching an auditor is the one failure that can't be walked back.

## Layers
1. **Raw sources** (immutable) — verified, agreed regulatory + project sources. Read, never edited.
2. **Wiki pages** (`pages/`) — model-owned summaries/entities/concepts, fully cross-referenced.
3. **Schema** — `CLAUDE.md` carries the iteration ritual (§XI); `WIKI.md` carries the wiki's
   shape (§9). Both must mirror the daily rule above; this README is the operational front door.

## Canon rule (what may enter)
Only verified knowledge + agreed sources. Every regulatory value carries both a primary source
(statute / O.Reg / HTA) and confirmed secondary corroboration; on conflict, primary and statute
win (RULES §10). Unverified material lives in `pages/staging/` flagged "not yet canon" and never
silently becomes fact.

## Autonomy boundary
- Model **auto-owns bookkeeping only**: drafting/updating pages, cross-refs, index/log, flagging
  contradictions.
- **Gary is the single required contact for every decision.**
- Compliance values stay **❓** until **Brian** certifies — through Gary. The model never writes
  ✅/❌ on its own and never contacts Brian.
- **Promoting** a lesson into `CLAUDE.md`/`RULES.md` (tightening the bar) is **Gary-only**.

## Lint (anti-staleness — prompted, not automatic)
On Gary's trigger, an adversarial pass hunts the maintainer's own drift — superseded claims,
values that crept off the certified set, orphan pages, missing cross-refs. Lint proposes;
Gary/Brian dispose.

## Uploading changes
Use GitHub Desktop (see PUSH.md): drop the changed file into the local folder, Commit, Push.
No terminal, no tokens, and folders are preserved.
