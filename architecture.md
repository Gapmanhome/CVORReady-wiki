# Architecture
_Last updated: 2026-05-24_

## System overview

Three products, one engine. ExeSketch is the shared infrastructure. CVORReady and BrokerShield are the forward-facing products that sit on top of it.

```
ExeSketch (engine)
  ├── MCP Server: cvor-assistant (7 tools)
  ├── MCP Server: carrierready (10 tools)
  ├── Document Library (70 documents)
  ├── Enforcement Workflows (SOPs)
  └── PDF Generator

CVORReady (compliance platform)
  ├── Admin Dashboard
  ├── Carrier Management
  ├── Document Generation
  ├── Manual Builder
  ├── Compliance Assistant (3-layer AI)
  └── Super Admin Architecture

BrokerShield (broker liability tool)
  ├── Carrier Check API
  ├── Dashboard (6 pages)
  ├── Chrome Extension
  ├── Webhook Receiver + SSE
  └── Marketing Site
```

## Tech stack

**ExeSketch:** Node.js / TypeScript, Replit, PostgreSQL (Neon), Drizzle ORM
**CVORReady:** Node.js / TypeScript (API), React / TypeScript (platform), Clerk (auth), Replit
**BrokerShield:** Shares ExeSketch server, React frontend

## ExeSketch MCP architecture

MCP (Model Context Protocol) is the core architectural decision. Knowledge is exposed as callable tools, not as searchable chunks. This means:
- Every answer is regulation-cited and specific
- Tools can be called by any Claude user in 2 minutes
- CVORReady's compliance assistant calls them automatically

**CVOR Assistant tools (7):**
- `check_cvor_score_risk` — CVOR scoring formula, rating thresholds, upgrade path
- `explain_mto_audit` — per-profile thresholds, fail-any-profile rule, common violations
- `get_compliance_checklist` — 5 scenarios including incident_response and load_securement
- `lookup_nsc_standard` — NSC Standards 1-15 full content
- `explain_incident_reporting` — 5 scenarios, $5,000 threshold, MOL number, obligations
- `explain_insurance_requirements` — Ontario $2M, FMCSA $750K, BOC-3, owner-operator WSIB
- `evaluate_driver_file` — driver qualification file requirements

**CarrierReady tools (10):**
- `list_jurisdictions` — 22 jurisdictions, Canada and US
- `explain_regulation` — any NSC standard or regulation in plain language
- `assess_audit_readiness` — carrier readiness for NSC Standard 15 audit
- `check_dispatch_clearance` — pre-dispatch enforcement gate
- `evaluate_hos_status` — HOS compliance under Canadian NSC and US FMCSA
- `explain_hos_rule` — any HOS rule explained
- `calculate_border_crossing_window` — Canada-US border crossing timing
- `generate_hos_audit_summary` — structured HOS compliance summary
- `generate_compliance_document` — generate any of 70 documents as PDF
- `get_document_requirements` — required documents for a given scenario

## CVORReady compliance assistant — three knowledge layers

The compliance assistant is the senior advisor for Michael's team. It has three knowledge layers that work together on every message:

**Layer 1 — Carrier context (injected into every message)**
Fetched from `GET /api/platform/admin/carriers/:id/assistant-context`. Contains: fleet profile, every driver by name with document statuses (licence, medical, abstract, annual review, TDG), vehicle annual inspection status, criticalIssues array, upcomingExpirations array with exact day counts.

**Layer 2 — Regulatory knowledge (ExeSketch MCP)**
Both ExeSketch MCP servers called on every message. CVOR regulatory knowledge + CarrierReady compliance tools. Answers are regulation-cited and specific.

**Layer 3 — Document content (CVORReady local MCP)**
`get_document_content` tool hosted at `/api/mcp/carrierready-docs`. Returns full section-by-section content of any of the 70 documents including checklist items, form fields, advisor notes, regulatory citations, retention periods.

**API:** Direct Anthropic API (not Replit proxy — proxy rejected `mcp_servers` parameter)
**Model:** `claude-sonnet-4-6`
**Auth:** `anthropic_api_key` secret in Replit
**MCP auth:** `EXESKETCH_API_KEY` as Bearer token

## CVORReady auth architecture

**Auth provider:** Clerk
**Session timeout:** 4 hours inactivity, 24 hours absolute maximum
**Client-side:** `useInactivityTimeout` hook, 15-minute warning modal with countdown
**Super admin:** `cvorready@gmail.com` — seeded idempotently on every server startup
**Role tiers:** `super_admin` | `admin`
**Suspension:** Suspended accounts blocked at login, token not issued
**Super admin immutability:** Cannot be suspended, deleted, or created via any API endpoint — seed only

## Document library

70 verified compliance documents across 8 categories. All content lives in `artifacts/api-server/src/data/carrierready-content.ts`. Generated as PDFs via `generate_compliance_document` MCP tool or directly via `/api/carrierready/generate-pdf`.

Categories: Driver Qualification (14), Vehicle Maintenance (8), Hours of Service (7), Load Securement (8), Roadside Inspection (4), Company Policies (15), Carrier Safety (10), Dangerous Goods (4).

See: [[document-library]]

## BrokerShield architecture

**Carrier check:** DOT/MC number → FMCSA safety data + insurance verification → PASS/CONDITIONAL/BLOCKED decision
**Chrome extension:** MV3 manifest, DOT/MC regex detection, badge injection, MutationObserver for SPAs, Rose Rocket selectors
**Webhook receiver:** POST `/api/bs/webhooks/rose-rocket/:brokerageId` — auto-check when carrier assigned in Rose Rocket
**SSE:** Real-time alert streaming per brokerage, auto-cleanup
**MCP:** `exesketch.com/mcp/brokershield` — 8 tools, any Claude user can connect

## Key architectural decisions

| Decision | Choice | Rationale |
|---|---|---|
| Auth provider | Clerk | Managed auth, Replit-compatible, invite flow built-in |
| Database | Neon PostgreSQL + Drizzle | Serverless-compatible, type-safe ORM |
| AI proxy | Direct Anthropic API | Replit proxy rejected mcp_servers parameter |
| Knowledge architecture | MCP tools | Precise regulation-cited answers vs probabilistic RAG |
| Document content | Local MCP server | CVORReady calls itself — no dependency on ExeSketch endpoint |
| Super admin | Seed on startup | No API can create super_admin — root of trust |
| Session security | Inactivity timeout | More reliable than window-close detection |
