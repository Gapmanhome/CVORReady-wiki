# Start here

The one file to read first each session. 30 seconds to orient, then go to `index.md`.

## What this repo is
A learning-loop wiki. Every session reads it, then writes back the smallest useful trace, so the
next session inherits what was learned instead of re-deriving it. The repo is the memory; the model
is not. (Full version: `README.md`.)

## Last session
**2026-06-30** — Efficiency restructure (proposed, awaiting Gary's push):
- `regulatory-knowledge.md` made the canonical value store; value pages are now thin pointers.
- `index.md` is now derived from page front-matter; collision threshold reconciled to ✅.
- This file (`START-HERE.md`) and `LINT.md` added.

## What's owed (the live worklist)
The only things that genuinely must carry across sessions. Knock these down, don't re-discover them.

- [ ] **Staging Mirage sweep** — class hit 3 instances; `sweep_done: false`. Owed per the rule.
- [ ] **Medical-exam interval — 730 d (system) vs MTO 1095 d.** ❓ HIGH priority — possible
      contradiction, touches the scoring engine. Confirm before treating as settled.
- [ ] **❓ values awaiting Brian (via Gary):** HOS log-audit interval · O. Reg. 638A mentorship ·
      30-day accident-preventability window · document-retention conventions · Ontario HOS set-fine.
- [ ] **`$19,277`** — bad string removed; correct replacement value / disposition still unknown.
- [ ] **Schema drafts unmerged** — CLAUDE.md §XI (iteration ritual) and WIKI.md §9 (wiki shape)
      are still PROPOSED in `schema/`. Cited around the repo as if live; not canon until Gary merges.
- [ ] **Dead-End Extraction** and **Half-Rendered Change** — each at 1 instance, sweeps not yet run.

## The gates (don't let efficiency leak into these)
- Model auto-owns **bookkeeping only** (drafting pages, cross-refs, index/log, flagging).
- **Gary** gates every decision and does every commit/push. The model never publishes.
- Compliance values stay **❓ until Brian certifies — through Gary.** The model never writes ✅/❌
  itself and never contacts Brian.
- Promoting a lesson into `CLAUDE.md` / `RULES.md` is **Gary-only**.
