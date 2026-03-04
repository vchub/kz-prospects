# Magnum RMN (Project Alpha) - Implementation Plan

Scope: Offline/Phygital RMN only (digital e-commerce inventory is controlled by Kaspi). The plan assumes Magnum owns in-store screens, smart scales, and the Magnum Club app, and focuses on measurable in-store media tied to loyalty data.

## 1) Goals and Success Metrics
- Monetize physical store traffic with measurable media packages for FMCG suppliers.
- Build a data and ad-serving layer that is independent of Kaspi.
- Prove closed-loop attribution for offline sales.

Primary KPIs
- Media revenue per store per month
- Incremental sales lift for promoted SKUs (test vs control)
- Ad fill rate and CPM/CPA targets
- Loyalty opt-in and active audience size
- Campaign setup time (self-service readiness)

## 2) Phased Execution Plan

Phase 0 - Alignment and Governance (4-6 weeks)
- Define RMN unit with clear P&L, staffed by product, data, engineering, and sales.
- Legal review: confirm what customer data can be used in offline RMN without violating JV constraints.
- Vendor shortlist for signage CMS, ad server, and CDP (build vs buy decision).

Phase 1 - Data Foundation (8-12 weeks)
- Create a unified shopper ID for offline data (loyalty card + phone hash).
- Standardize product catalog IDs across POS, inventory, and pricing systems.
- Build a minimal CDP: segments based on purchase history and store location.
- Stand up a privacy layer: consent management and data minimization.

Phase 2 - In-Store Inventory Activation (10-14 weeks)
- Upgrade smart scales and LED screens to be addressable endpoints.
- Deploy a lightweight ad decisioning service (rules-based first, ML later).
- Start with 10-20 pilot stores in Almaty/Astana; measure lift.

Phase 3 - Loyalty + Mobile Triggering (8-12 weeks, overlaps Phase 2)
- Add in-store geofencing via app (opt-in only) to deliver push offers.
- Launch real-time “basket-aware” triggers at checkout (coupon codes).
- Validate closed-loop attribution using loyalty ID.

Phase 4 - Self-Service Portal (12-16 weeks)
- Supplier portal for booking impressions and uploading creatives.
- Basic reporting dashboard: impressions, reach, sales lift, ROAS.
- Pricing model: CPM for screens, CPA/CPS for targeted offers.

Phase 5 - Scale (ongoing)
- Expand to 100+ stores and additional formats.
- Add dynamic creative optimization and seasonal triggers.
- Introduce off-site activation only if JV constraints allow.

## 3) Software Architecture (High-Level)

Core Systems
- Data ingestion: POS, loyalty, inventory, and pricing feeds.
- CDP/Segment store: audience segments and shopper profiles.
- Ad decisioning: rules engine, later ML-based.
- Content delivery: signage CMS and device management.
- Measurement: attribution pipeline and reporting.

Reference Architecture
1) Data Ingestion Layer
- POS events (near real-time)
- Loyalty events (app + card scans)
- Product catalog (SKU master)
- Store metadata (location, format)

2) Identity and CDP
- Shopper ID service (hash phone, map loyalty ID)
- Segment builder (RFM, category affinity, basket patterns)
- Consent registry (opt-in flags)

3) Ad Serving and Rules
- Campaign rules engine
- Inventory scheduler (screens, time slots)
- Frequency capping per shopper

4) Delivery Channels
- In-store screens (LED, shelf-edge, scales)
- Mobile app push notifications
- Optional: in-store Wi-Fi landing page

5) Measurement
- Control vs exposed cohorts
- Sales lift per SKU
- Campaign ROAS and attribution windows

Suggested Tech Stack (agnostic)
- Event streaming: Kafka/PubSub
- Storage: Postgres for metadata, ClickHouse/BigQuery for events
- API layer: GraphQL/REST
- Ad decisioning: custom rules engine + Redis cache
- Dashboard: Metabase/Looker

## 4) Access to 3rd-Party APIs and Integrations

Required Integrations
- Signage CMS API (device inventory, content scheduling)
- Push notification service (Firebase/APNS)
- POS integration (Magnum internal or vendor API)
- Loyalty platform API (Magnum Club)
- Inventory and catalog system (Symphony RetailAI or equivalent)

Optional Integrations
- Mobile wallet or payment partners for offer redemption (if allowed)
- External ad measurement partner (brand lift surveys)
- Geofencing SDK (if app supports location permissions)

API Access Workstreams
- Identify data ownership and access rights in JV agreements.
- Create a vendor-neutral API gateway to avoid lock-in.
- Build a sandbox for suppliers to test creatives and reporting.

## 5) Marketing Strategy (Pros and Cons)

Positioning
- “Offline RMN with deterministic attribution” for FMCG brands.
- “Phygital conversion” for suppliers that need in-store lift.

Pros
- Exclusive access to in-store conversion data (offline closed-loop).
- High shopper intent at point of purchase.
- Lower competition vs Kaspi digital inventory.
- Premium placement opportunities (checkout, scales, shelf-edge).

Cons
- Hardware CapEx and maintenance at scale.
- Slower campaign setup vs pure digital platforms.
- Requires strong sales enablement to shift trade marketing budgets.
- Limited digital reach outside store walls.

Launch Marketing Plan
- Pilot case studies with 2-3 top FMCG brands.
- Bundle pricing to replace part of existing trade marketing fees.
- “Guarantee” offers (e.g., minimum impressions or rebate).
- Joint PR with suppliers to validate measurable lift.

## 6) Risk Register and Mitigations
- JV data restrictions: focus on offline-only assets; legal review early.
- Operational complexity: start with limited store footprint.
- Low advertiser adoption: co-design packages with top suppliers.
- Data quality issues: enforce SKU and store ID normalization.

## 7) Deliverables
- RMN business unit charter
- MVP CDP + segment definitions
- Pilot store rollout plan
- Supplier portal MVP and reporting dashboards
- First 3 brand case studies with lift analysis
