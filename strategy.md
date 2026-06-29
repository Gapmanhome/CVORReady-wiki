# Strategy
_Last updated: 2026-05-24_

## Core thesis

ExeSketch is operational decision enforcement infrastructure for regulated industries. The thesis is "Intel Inside" — ExeSketch is the substrate that powers multiple forward-facing products. Carriers, brokers, advisors, and inspectors never interact with ExeSketch directly. They interact with CVORReady, BrokerShield, or future verticals. ExeSketch is the engine underneath all of them.

The moat is not the UI. It is the verified, regulation-cited knowledge base and the MCP architecture that makes it callable by any AI agent. By the time a competitor builds what ExeSketch has built, the knowledge base will be two years deeper.

## Products

### CVORReady
Ontario commercial carrier compliance platform. Sold to compliance advisors (not directly to carriers). The advisor uses CVORReady to manage their entire client portfolio — document generation, manual building, compliance tracking, and AI-assisted advisory.

**Pricing:** $499/month per advisor account.
**Model:** B2B SaaS to compliance advisors. Each advisor manages 10-50 carrier clients. This is a force multiplier — one CVORReady customer brings their entire book of business.
**Status:** Live. First customer paying. Second and third signing.

See: [[commercial-pipeline]], [[architecture]]

### BrokerShield
Ontario freight broker liability tool. Emerged from the Montgomery v. Doak ruling (Supreme Court of Canada, 9-0) which established broker liability for carrier negligence. BrokerShield checks carriers against safety and insurance data before dispatch, creates a defensible audit trail.

**Pricing:** TBD — validated but not yet priced.
**Model:** Direct to freight brokers. Per-check or subscription.
**Status:** Fully built. Three validated broker conversations. Zero signed contracts.
**Integration path:** Level 1 — webhook receiver (Rose Rocket auto-check). Level 2 — Chrome extension (any web TMS). Level 3 — Rose Rocket Platform Partner (requires 3-5 paying customers first).

See: [[commercial-pipeline]], [[architecture]]

### ExeSketch (platform)
The enforcement and document generation engine. Not sold directly. Powers CVORReady and BrokerShield. Accessible to any Claude user via MCP — connect in 2 minutes at exesketch.com.

**MCP servers live:**
- `exesketch.com/mcp/cvor-assistant` — 7 tools, CVOR regulatory knowledge
- `exesketch.com/mcp/carrierready` — 10 tools, compliance document generation

See: [[architecture]]

## Revenue model

```
CURRENT:
  CVORReady — $499/month per advisor
  BrokerShield — $0 (not yet priced)
  ExeSketch MCP — free (lead generation)

TARGET (12 months):
  CVORReady — 10 advisors × $499 = $4,990/month
  BrokerShield — 5 brokers × TBD
  ExeSketch — potential enterprise licensing

THE MULTIPLIER EFFECT:
  One CVORReady advisor at $499/month
  manages 10-50 carrier clients
  Each carrier client pays the advisor
  ~$2,000-5,000/year for compliance programs
  CVORReady makes that advisor 10x more efficient
  The advisor's ROI on $499/month is immediate
```

## Competitive position

No direct competitor builds the combination of:
- Verified Ontario regulatory knowledge base (NSC Standards 1-15, HOS, incident reporting, CVOR scoring, insurance requirements, load securement)
- 70-document compliance library with full content
- AI compliance assistant with three knowledge layers (carrier context + regulatory MCP + document content)
- Enforcement workflow engine (ExeSketch SOPs)
- Broker liability tool (BrokerShield)

The closest competitors are generic compliance SaaS tools that lack the Ontario-specific regulatory depth and have no AI advisory capability.

## Strategic decisions made

- **Advisory model over direct-to-carrier** — selling to advisors gives distribution leverage and avoids the carrier sales cycle (long, relationship-dependent). Advisors come with portfolios.
- **MCP over RAG** — the knowledge base is callable as tools, not searched as chunks. This gives precise, regulation-cited answers rather than probabilistic retrieval.
- **$499/month fixed** — not usage-based. Advisors need predictable costs. Usage-based pricing creates friction on every client interaction.
- **Build BrokerShield fully before first sale** — product is complete. Commercial validation came through conversations, not a waiting list.

## Open questions

- BrokerShield pricing — what is the right model? Per-check, monthly subscription, or enterprise annual?
- Rose Rocket partnership — apply after 3-5 BrokerShield customers paying
- White-label CVORReady for non-NextGen advisors — preparedBy field should be per-account, not hardcoded

See: [[open-issues]]
