# Open Issues
_Last updated: 2026-05-24_

Append-only log of unresolved decisions, pending work, and known gaps. Update when resolved — do not delete entries, mark them RESOLVED with date.

---

## OVERDUE — Commercial

### [COMMERCIAL-001] NextGen case study unpublished
- **Status:** OVERDUE
- **Priority:** Critical — this is the primary commercial asset
- **Details:** Copy written. Name and logo approved. First invoice paid. No blockers.
- **Action:** Publish on exesketch.com and cvorready.com immediately.
- **Opened:** Session 4
- **Blocker:** None

### [COMMERCIAL-002] BrokerShield pricing not set
- **Status:** Open
- **Priority:** High — blocks sending proposals to 3 validated brokers
- **Options:** Per-check, monthly subscription, annual enterprise
- **Decision needed:** What model fits broker workflows best?
- **Opened:** Session 6

---

## Product — CVORReady

### [CVORREADY-001] Manual cover page — NextGen logo / preparedBy
- **Status:** Open — decision deferred
- **Details:** Cover page shows client logo at top, "Prepared by: NextGen Safety and Compliance" at bottom. Question: should NextGen's logo appear on the cover co-branded with client logo? Currently only text "Prepared by" not a logo.
- **Decision needed:** Does Michael want NextGen logo on cover or is text sufficient?
- **Second issue:** preparedBy is currently per-account but should be confirmed as configurable — if other advisors ever use CVORReady their name must show, not NextGen's.
- **Opened:** Session 5

### [CVORREADY-002] Session timeout implementation
- **Status:** SPRINT WRITTEN — pending delivery
- **Details:** 4-hour inactivity timeout with 15-minute warning modal and countdown. Clerk session settings + client-side useInactivityTimeout hook.
- **Sprint:** Written in session 6. Paste to CVORReady Replit Agent.

### [CVORREADY-003] Super admin team management
- **Status:** DELIVERED ✅
- **Resolved:** Session 6 — full super admin architecture live

---

## Product — BrokerShield

### [BROKERSHIELD-001] PWA (mobile coverage)
- **Status:** Deferred
- **Priority:** Low — desktop workflow is primary for brokers
- **Details:** Mobile-responsive PWA for brokers checking carriers on the go.
- **Timing:** After first paying customer

### [BROKERSHIELD-002] Rose Rocket Platform Partner application
- **Status:** Deferred
- **Priority:** Medium — unlocks deeper integration and distribution
- **Timing:** After 3-5 paying BrokerShield customers
- **Note:** Chrome extension already covers Rose Rocket web UI without partnership

---

## Technical

### [TECH-001] Document content tool on ExeSketch public MCP endpoint
- **Status:** NOT REQUIRED — resolved by architecture
- **Details:** get_document_content tool lives in CVORReady (calls itself). Does not need to be on exesketch.com/mcp. CVORReady compliance assistant calls all three MCP servers correctly.

### [TECH-002] Session timeout sprint delivery
- **Status:** SPRINT WRITTEN — pending delivery
- **Sprint location:** Session 6 transcript
- **Action:** Paste sprint to CVORReady Replit Agent

---

## Knowledge base

### [KB-001] Document content knowledge base gap
- **Status:** RESOLVED ✅ — Session 6
- **Resolution:** get_document_content MCP tool built. Full content of all 70 documents accessible. Three verification tests passed (CR-DQ-014, CR-VM-008, CR-POL-010).

### [KB-002] This wiki — initial build
- **Status:** DELIVERED ✅
- **Details:** Five seed wiki pages created: strategy, architecture, regulatory-knowledge, commercial-pipeline, open-issues.

---

## Resolved log

| Issue | Resolution | Session |
|---|---|---|
| MCP integration blocked by Replit proxy | Switched to direct Anthropic API | Session 6 |
| Compliance assistant document gap | get_document_content tool built | Session 6 |
| Super admin architecture | Full implementation delivered | Session 6 |
| 10/10 MCP knowledge expansion tests | All passing | Session 6 |
| First CVORReady invoice | Paid by NextGen | Session 6 |
