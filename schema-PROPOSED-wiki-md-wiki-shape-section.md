# PROPOSED addition to WIKI.md — review and merge (do not auto-apply)

Insert as a new section §9. Describes the learning-loop wiki's shape (the human reference for it).

---

## 9. THE LEARNING-LOOP WIKI (compounding knowledge)

The §7 learning loop, made a persistent interlinked knowledge base. One job: every iteration
writes what it learned back, so the next inherits it instead of re-deriving it.

### 9.1 Page types
- **Value pages** (`pages/values/`) — one per regulatory value: figure, old->new, primary +
  secondary source, ✅/❌/❓ status, Brian-certified flag, forms that use it. This is the
  compliance value ledger, cross-referenced. Brian's certification list seeds these.
- **Class pages** (`pages/classes/`) — one per named bug-class (Orphaned Override, Dead-End
  Extraction, Staging Mirage, Half-Rendered Change, plus Karpathy's). Each lists its instances
  and its sweep. **Third instance triggers a denominator-establishing sweep** (§7.2).
- **Prompt-shape pages** (`pages/prompts/`) — the prompt structures that reliably worked, with
  when-it-worked evidence (the PROMPTS.md library).
- **Domain pages** (`pages/domains/`) — A–G state + regression tests + open items.

### 9.2 Index + log
`index.md` is the content catalog (read first on query). `log.md` is the append-only timeline,
prefixed `## [YYYY-MM-DD] <kind> | <title>` so `grep "^## \[" log.md | tail -5` works.

### 9.3 Canon vs staging
Only verified knowledge + agreed sources are canon. Every value carries a **primary** and a
confirmed **secondary** source. Unverified material lives in `pages/staging/` flagged not-canon
until promoted (primary + secondary confirmed; values also need Brian via Gary).

### 9.4 Maintainer + autonomy
The **reviewing model** maintains the wiki (it is synthesis, on the review side of the
execution/review line — not codebase execution). It auto-owns bookkeeping only; **Gary is the
single required contact for every decision**; **Brian** certifies values *through Gary*;
promotion into CLAUDE.md/RULES is **Gary-only**.

### 9.5 Lint (anti-staleness, prompted)
On Gary's trigger, an adversarial lint pass hunts the maintainer's OWN drift — superseded claims,
values that crept off the certified set, orphan pages, missing cross-refs — and **proposes** to
Gary/Brian. This is the wiki's standing guard against the AI-reviewing-AI lenient drift the RQGM
note warns about (over-acceptance up to 1.91x). The evaluator must rise as the agent improves,
never freeze.
