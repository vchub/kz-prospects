# Analysis of `influencer/search/` + 3 MVP Variants

**Date:** March 5, 2026
**Inputs reviewed:** `cis.md`, `global-search-2026-03-04.md`, `global2.md`, `global3.md`

## 1) Critical analysis of current search results

### What is strong
1. Consistent signal across files: market shifted from vanity metrics to commerce outcomes.
2. Repeatable winning bundle appears in both CIS and global reports:
- workflow orchestration,
- hybrid compensation,
- multi-method attribution,
- payout/compliance,
- fraud controls,
- ROI reporting.
3. Regional constraint is clear and practical: partial attribution in closed ecosystems (Kaspi/Uzum) requires promo-code + CRM reconciliation + pre-lander patterns.

### What is weak / risky in the dataset
1. Source quality is uneven.
- `global-search-2026-03-04.md` is the most reliable artifact because claims are linked.
- `global2.md` and `global3.md` include many high-confidence statements but mixed sourcing and some likely over-precise claims.
2. Some case lists in `global3.md` mix true platform failures with unrelated brand/legal scandals, which weakens causal clarity.
3. Several numeric claims in `cis.md` and `global3.md` look plausible but are not always independently verified in-file.

### Working assumptions to carry forward
1. Build for attribution-imperfect environments by default.
2. Discovery is not a moat; operations + payouts + compliance are.
3. Pure CPA-only model is fragile for creator adoption in CIS; hybrid deals are needed.
4. For global scale, ecommerce-stack integrations (Shopify/Woo + GA4-like attribution) become table stakes.

## 2) Three MVP variants

## Variant A: CIS Brandformance Core (KZ/UZ-first)
**Positioning:** Operational and financial infrastructure for micro/nano creator campaigns in closed-commerce environments.

**Target users:** Local SMEs, regional agencies, micro creators.

**MVP scope (minimal):**
1. Campaign brief + creator assignment + approval flow.
2. Hybrid deal setup: fixed + CPA/CPC/bonus.
3. Attribution primitives:
- promo code generator,
- trackable short links,
- pre-lander click logging,
- manual/CSV CRM reconciliation.
4. Creator wallet with payout status.
5. Compliance basics:
- ad-label checklist,
- contract templates,
- payout statement export.
6. Core analytics: cost, clicks, validated orders, payout, ROI estimate.

**Why this should work (from reports):**
- Matches CIS constraints and Perfluence-like performance expectations.
- Solves two top anxieties: brand ROI uncertainty + creator payout/tax friction.

**Do not build in MVP:**
- influencer discovery marketplace,
- advanced AI agents,
- full tax filing automation with government integrations.

**Primary risk:** High manual ops load for reconciliation.

## Variant B: Commerce OS Lite (Global D2C)
**Positioning:** Lightweight creator performance operating system integrated into merchant analytics and store stack.

**Target users:** D2C brands already on Shopify/WooCommerce.

**MVP scope (minimal):**
1. Creator campaign workflow (briefing, approvals, delivery tracking).
2. Link + code attribution tied to store orders.
3. Basic GA4 event mapping (session/campaign/source to conversion).
4. Automated payout calculation by creator and campaign.
5. Rights usage flags for paid amplification.
6. Brand dashboard: revenue attributed, CAC proxy, creator ranking.

**Why this should work (from reports):**
- Aligns with CreatorIQ/GRIN/Later pattern: integration with merchant core stack.
- Stronger defensibility than pure matching tools.

**Do not build in MVP:**
- social-native live streaming infra,
- fully autonomous AI negotiation,
- multi-country tax engine.

**Primary risk:** Integration complexity and data consistency across store + analytics.

## Variant C: Live Commerce Studio Lite (Channel-led)
**Positioning:** Managed live-shopping campaign OS, not a social network.

**Target users:** Brands with frequent drops/promotions; creators with strong livestream engagement.

**MVP scope (minimal):**
1. Live campaign templates (pre-live brief, runbook, offer ladder).
2. Shoppable link set per stream segment/product.
3. Real-time stream console:
- pinned offers,
- coupon/offer timing,
- moderator checklist.
4. Post-live replay package with tracked links/codes.
5. Performance report: live viewers, clicks, conversion events, payout.
6. Hybrid creator payout (flat live fee + performance bonus).

**Why this should work (from reports):**
- Captures trend toward commerce-native creator formats.
- Uses existing channels/platforms instead of building a new consumer app.

**Do not build in MVP:**
- in-app checkout,
- proprietary streaming CDN,
- full warehouse/logistics stack.

**Primary risk:** Heavy dependence on external channel rules and API/policy changes.

## 3) How to choose among the 3 variants

Pick **Variant A** if immediate market is Kazakhstan/Uzbekistan SMEs and creator liquidity is the key wedge.

Pick **Variant B** if your fastest path is D2C brands that already demand CFO-grade attribution and store integrations.

Pick **Variant C** if you have strong access to creators/brands who can run repeat live-sales formats weekly.

## 4) Recommended default

Based on current CIS + global evidence quality, the safest starting point is:
- **Variant A first**,
- with a clean upgrade path to **Variant B** integrations,
- and **Variant C** as a vertical module for high-performing categories.

This sequence minimizes platform risk while building durable operational moats.
