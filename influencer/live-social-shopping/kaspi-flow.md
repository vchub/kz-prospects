# Kaspi Flow Analysis for Live Social Shopping

**Run date:** March 4, 2026  
**Method:** Critical assumption check with web sources (primarily Kaspi official partner docs)

## Initial idea (tested)
Use our own Kaspi storefront as a proxy seller for brand products promoted by influencers in live streams, with creator-specific product labels as a promo-code analog.

## Verdict (short)
**Possible in a narrow merchant-of-record format, but high operational and policy risk if implemented as "label hacks".**

- Feasible: operating a Kaspi store, adding products, processing orders, paying creators.
- Risky: duplicative/mislabeled product-card strategy and "complete analytics" expectation.
- Not supported by evidence: guaranteed ability to "circumvent Kaspi wall" without constraints.

## Assumption-by-assumption check

1. "We can register and run a Kaspi storefront"
- **Status:** Valid.
- Evidence: seller eligibility and Kaspi Pay requirements are documented.
- Source: https://guide.kaspi.kz/partner/ru/shop/conditions/q1338

2. "We can create products/cards for campaign tracking"
- **Status:** Partially valid.
- You can add products and use API for product operations.
- But card integrity is controlled; duplicates/misclassification can be removed.
- Sources:
  - https://guide.kaspi.kz/partner/ru/shop/goods/add/q2223
  - https://guide.kaspi.kz/partner/ru/shop/api/goods/q3223
  - https://guide.kaspi.kz/partner/ru/shop/goods/delete/q3246

3. "We can use specially labeled products as promo-code analog"
- **Status:** High risk.
- Rules require delivering exactly what is in the order/card and prohibit misleading practices.
- Inflated/abnormal pricing and manipulative behavior are sanctionable.
- Source: https://guide.kaspi.kz/partner/ru/shop/conditions/q1342

4. "Influencer sends traffic to our Kaspi product links"
- **Status:** Generally feasible externally.
- But this does not by itself guarantee full-funnel attribution inside Kaspi ecosystem.
- Source context: Kaspi seller tooling/docs focus on order operations, not full external influencer attribution.

5. "We forward fulfillment to original store/brand"
- **Status:** Possible only with strict control and contracts.
- Kaspi partner remains accountable for delivery quality, returns handling, and buyer communication standards.
- Source: https://guide.kaspi.kz/partner/ru/shop/conditions/q1342

6. "We get complete analytics and data"
- **Status:** Invalid as stated.
- You can get order-level seller analytics, but not complete cross-channel user journey data.
- Any claim of "complete analytics" is an overstatement.

7. "We circumvent Kaspi wall"
- **Status:** Overstated.
- You may improve attributable signal via merchant-of-record links/SKUs, but not fully bypass ecosystem attribution limits.

8. "We remove tax/payment burden from original store"
- **Status:** Conditionally valid.
- If you become merchant-of-record and pay creators yourself, yes.
- Tradeoff: you inherit tax/compliance, refunds, quality claims, and reputational risk.

## Critical risks

1. Policy/compliance risk
- Product-card manipulation can trigger restrictions or disconnection.
- Source: https://guide.kaspi.kz/partner/ru/shop/conditions/q1342

2. Returns/warranty risk
- End-customer disputes are handled against the seller account; proxy architecture concentrates liability.
- Source: https://guide.kaspi.kz/client/ru/shop/returns/general/q16184

3. Unit economics risk
- Added reseller layer increases margin pressure (delivery, cancellation, returns, support overhead).
- Delivery tariff updates in 2026 reinforce this pressure.
- Source: https://guide.kaspi.kz/partner/ru/shop/delivery/shipping/q2288

4. Attribution confidence risk
- Better than pure external promo-code only, but still not "complete".

## Safer model variants

### Variant A: Strict merchant-of-record model (recommended if using Kaspi)
- Only list SKUs you can legally and operationally fulfill under SLA.
- No fake/duplicate card naming tricks; keep catalog integrity.
- Track creator performance via controlled SKU batches + external click IDs where possible.

### Variant B: Hybrid model (Kaspi + off-platform attribution)
- Kaspi for transaction convenience.
- External pre-lander/offer page for campaign attribution and creator routing.
- Accept partial attribution and optimize payout formulas accordingly.

### Variant C: Non-Kaspi-first for live commerce attribution
- Use channels/shops where tracking primitives are stronger, keep Kaspi as distribution endpoint, not attribution core.

## Recommendation
**Proceed only with Variant A/B assumptions, not with a "wall circumvention" promise.**

Positioning that is defensible:
- "Operational simplification for brands + structured creator payouts + better (not complete) attribution."

Positioning to avoid:
- "Full attribution and guaranteed policy-safe circumvention of Kaspi constraints."

## Sources used
- Kaspi seller eligibility: https://guide.kaspi.kz/partner/ru/shop/conditions/q1338
- Kaspi rules and prohibited behavior: https://guide.kaspi.kz/partner/ru/shop/conditions/q1342
- Add products/cards: https://guide.kaspi.kz/partner/ru/shop/goods/add/q2223
- API product schema/import context: https://guide.kaspi.kz/partner/ru/shop/api/goods/q3223
- Duplicate-card handling: https://guide.kaspi.kz/partner/ru/shop/goods/delete/q3246
- Returns dispute flow: https://guide.kaspi.kz/client/ru/shop/returns/general/q16184
- Delivery cost framework: https://guide.kaspi.kz/partner/ru/shop/delivery/shipping/q2288
- Partner documents index: https://guide.kaspi.kz/partner/ru/shop/documents/
