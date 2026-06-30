# Lint — mechanical vs judgment

Lint is split in two. **Both only propose — neither ever auto-fixes.** Gary/Brian dispose.

## Mechanical lint (deterministic — run any session)
These are yes/no checks against the files themselves. Cheap, so run them often. They catch the
exact drift this repo has already produced. Run by eye, or wire into a script later if you go
terminal — the checks are the same either way.

1. **No orphan pages.** Every file under `pages/` is linked from `index.md`.
2. **Index == source.** Each value's status in `index.md` matches `regulatory-knowledge.md`.
   *(This is the bug that showed collision as ❓ in the index while the ledger said ✅.)*
3. **Value page == ledger.** Each `pages/values/*` status mirrors the ledger; ledger wins on conflict.
4. **Owed sweeps.** Any class page with `instances >= 3` and `sweep_done: false` → flag.
   *(Currently: Staging Mirage.)*
5. **Field-name consistency.** Pages use the same front-matter keys as their template
   (e.g. `certified_by` — the value template's `brian_certified` is the odd one out).
6. **Staging discipline.** No item promoted out of `pages/staging/` without primary + secondary
   confirmed (and, for values, Brian via Gary).
7. **Log floor.** `log.md` has an entry for the most recent session.

## Judgment lint (prompted — Gary triggers)
The adversarial pass: has a claim quietly gone stale, has a value crept off the certified set, is a
cross-ref missing in spirit rather than in form. This needs reasoning, not a checklist, so it stays
prompted-only — the standing guard against lenient AI-reviewing-AI drift. Mechanical lint can't
replace it; it just clears the cheap stuff out of its way.
