# Project Gamma (Influencer CPA Platform) - Implementation Plan

**Date:** February 1, 2026
**Based on:** Deep Search Report (Jan 31, 2026)
**Team:** Software Engineering & Marketing Strategy

---

## 1. Executive Summary
This document outlines the technical and go-to-market execution plan for "Project Gamma," a CPA (Cost-Per-Action) platform connecting Kazakhstan's micro-influencers with retailers (Wildberries, Magnum, Technodom).

**Core Value Prop:**
1.  **For Retailers:** Performance-based marketing (pay only for sales, not posts).
2.  **For Influencers:** Automated monetization of their audience + **Automated Tax Compliance** (solving the legal headache).

---

## 2. Software Architecture

### 2.1 High-Level Architecture
We will adopt a **Modular Monolith** architecture initially for speed of development, transitioning to **Microservices** as the tracking load scales. The system relies heavily on event-driven processing for attribution.

### 2.2 Core Components

#### A. The "Link Wrapper" (Deep Link Engine) - *The Core Tech*
*   **Function:** Takes a standard product URL (e.g., `wildberries.kz/catalog/123`) and wraps it in a tracking domain (e.g., `gamma.kz/click?ref=user_id&target=url`).
*   **Requirements:**
    *   < 50ms latency on redirects.
    *   Device fingerprinting (IP, User Agent) for probabilistic attribution fallback.
    *   Deep-linking capabilities (opening the target App instead of Browser if installed).

#### B. The Attribution Listener (Postback Handler)
*   **Function:** An endpoint that receives "Conversion Events" from Retailers.
*   **Protocol:** Server-to-Server (S2S) Postbacks.
    *   *Flow:* User Clicks Link -> Gamma records ClickID -> Redirects to Retailer with `?sub1=ClickID` -> User Buys -> Retailer Server fires Webhook to Gamma with `ClickID` + `Amount`.

#### C. The "Tax & Wallet" Ledger
*   **Function:** Manages virtual balances, separates "Pending" (return period) vs. "Available" funds, and calculates tax withholding.
*   **Logic:**
    *   Gross Commission: 1000 KZT
    *   Platform Fee (20%): -200 KZT
    *   Tax Withholding (10% - illustrative): -100 KZT
    *   Net Payout to Influencer: 700 KZT

### 2.3 Tech Stack Recommendation
*   **Backend:** **Node.js (TypeScript)** or **Go**. Node.js is preferred for rapid iteration; Go for the Redirect/Tracking microservice if traffic scales to millions of clicks.
*   **Database:**
    *   **PostgreSQL:** For users, wallets, and ledger (ACID compliance is critical for money).
    *   **ClickHouse:** For high-volume click/event analytics (reporting).
    *   **Redis:** For caching redirect rules and active session tokens.
*   **Frontend:**
    *   **Influencer App:** **Flutter** (Cross-platform iOS/Android). Micro-influencers operate primarily on mobile.
    *   **Brand Dashboard:** **React.js**.
*   **Infrastructure:** Containerized (Docker/Kubernetes). Hosted on local cloud (e.g., PS Cloud or VK Cloud) or AWS if latency/data residency permits.

---

## 3. Third-Party API Strategy

### 3.1 Wildberries (The "Wibes" Integration)
*   **Status:** Critical Dependency.
*   **Integration Point:** Wildberries API for Affiliates (Wibes).
*   **Data Needed:**
    *   Product Catalog (to allow influencers to search/pick items inside our app).
    *   Order Status (Pending -> Delivered -> Returned).
*   **Risk:** API stability. We must build a defensive "Status Polling" worker to verify order finalization if webhooks fail.

### 3.2 Retailer Direct Integrations (Magnum / Technodom)
*   **Challenge:** These players likely lack a standardized public Affiliate API.
*   **Solution:** We will provide a standard **"Gamma Pixel"** and **Postback Spec**.
    *   *Implementation:* Their tech team adds our Javascript SDK to their checkout success page, OR they configure their backend to fire a HTTP POST to us on successful payment.
*   **Alpha/RMN Leverage:** Use the existing Retail Media Network relations to force this technical integration priority.

### 3.3 Fintech & Tax (The "Safety" Layer)
*   **Partners:** **Wooppay**, **Qiwi**, or **Kassa24**.
*   **Integration:** "Mass Payouts" (Массовые выплаты).
*   **Tax Logic:**
    *   Verify User IIN (National ID).
    *   Check "Self-Employed" (ESP) or IP status via e-gov database (if accessible) or require upload of registration.
    *   *Automated Withholding:* We act as the tax agent. We deduct the tax *before* sending the net amount to the influencer's card.
    *   **API Call:** `Payout(Amount, Tax_Component, Destination_Card)`.

---

## 4. Marketing Strategy: Pros, Cons & The Pivot

### 4.1 The Pitch
*   **To Influencers:** "Stop chasing brands for payments. Promote what you love, get paid automatically, and **never worry about the Tax Office again**."
*   **To Brands:** "Access the 'Long Tail' of 5,000 influencers without managing 5,000 contracts. Pay only for Sales."

### 4.2 Pros (Why this wins)
1.  **The "Safety" Moat:** By handling the tax complexity (which is terrifying for a 19-year-old influencer), we lock them into our platform.
2.  **Unlocking Wildberries:** WB is growing fast. Influencers buy there anyway. Monetizing their "Hauls" is natural content.
3.  **Data Dominance:** We will own the conversion data for the non-Kaspi market, making us valuable to advertisers.

### 4.3 Cons (The Challenges)
1.  **The "Kaspi Wall" (Marketing impact):** Users *want* to buy on Kaspi. If we send them to Technodom, conversion rates will be lower. We must educate influencers to say "Link in bio for Technodom" specifically.
2.  **Cultural Friction:** Influencers are used to "Flat Fee" (getting paid 20k KZT just to post). Moving to "Earn 5% of sales" feels risky to them.
    *   *Mitigation:* Hybrid Model? (Small flat fee + Commission) for top performers.
3.  **Attribution Leakage:** Users click the link on mobile, app doesn't open deep-link correctly, or they switch devices. We will lose ~20-30% of sales tracking. This causes trust issues ("I sold 10, you tracked 5").

### 4.4 Launch Phases
*   **Phase 1 (The Wrapper):** Manual MVP. Select 50 influencers. Give them manually generated WB links. Track via manual WB report exports. Test payouts.
*   **Phase 2 (The App):** Launch Flutter app. Automated link generation. Integration with Wooppay. Open to top 500.
*   **Phase 3 (The Ecosystem):** Integrate Magnum/Technodom APIs. Open to all.

---

**Verdict:** The technical build is standard. The *business* complexity lies in the Fintech/Tax integration and the Sales Engineering required to get Retailers to implement our Postbacks.
