# Critical Analysis: ideas.md

Reviewed against `proposal/project_proposal.md` and known constraints.

---

## Idea 1 — Refund / Cashback Fallback

**Status: real risk, not just a nice-to-have idea.**

The proposal currently treats this as "open question." It should be treated as the primary fallback plan for a specific failure mode: partner code pools don't arrive on time or partners change terms.

What makes this viable in Kazakhstan: fiscal receipts from major retailers (Magnum, CU, Kaspi supermarkets) include a QR code that links to the official КГД (tax authority) database. This means receipt validation can be done programmatically — not by OCR guessing, but by querying a government-verified record. Kaspi Pay covers the refund payment rail for most of the target audience.

What makes this harder than it looks:
- Minor retailers may not have electronic fiscal receipt systems
- Receipt QR validation requires API access to КГД — needs to be scoped/tested
- Introduces two-step delay (buy → upload → validate → pay) vs instant redemption
- Brand gets "purchase proof" but loses the pre-purchase sampling intent signal

**Recommendation:** Specify this explicitly as Stage 2 fallback with a concrete trigger (e.g., "if less than 50% of code pools arrive 14 days before launch"). Don't leave it as an abstract option.

---

## Idea 2 — Is Telegram Identity Enough?

**Status: correct framing, but decision is deferred for the wrong reason.**

The proposal says "keep Telegram-only for pilot, add stronger checks if fraud appears." This is reasonable but incomplete. The question to answer before pilot: what is the acceptable fraud rate and what does it cost us?

If 1 voucher = 1 drink ≈ 400 KZT, and the total pilot budget is 10M KZT (25,000 drinks), then:
- 5% fraud = 1,250 extra drinks = 500,000 KZT waste
- 10% fraud = 2,500 extra drinks = 1,000,000 KZT waste

Telegram ID is good (stable, verified phone at registration, one account per device norm). Phone number sharing in bot is a stronger signal if needed. The question is whether the brand's tolerance for fraud waste justifies adding friction.

**What's missing from the proposal:** a concrete fraud budget — what % abuse is acceptable before stronger identity is required. Without this number, the decision to add or not add verification has no trigger condition.

**Recommendation:** Define the pilot fraud tolerance threshold explicitly. Telegram-only is likely fine for a controlled pilot with volume caps; document the threshold at which phone verification would be added.

---

## Idea 3 — Partner-Lock Rule Specification

**Status: product gap that will cause real problems if unresolved before launch.**

The current proposal describes the flow but doesn't answer:
- Can user cancel before code is issued? (Yes, trivially — just don't press the button)
- Can user reactivate with a different partner if TTL expires? (Not resolved — see the reactivation problem below)
- What if user selects Glovo but Glovo is temporarily unavailable? (No fallback specified)

The most critical unresolved case: user activates for Magnum, receives QR, 15 minutes pass. User claims "I didn't use it." System has no way to verify — the Magnum scanner may or may not have processed it. This is the fundamental integrity problem of operating without real-time POS integration.

**Recommendation:** Choose a policy explicitly before launch:
- Option A: Single activation, no reactivation. Code is consumed on issuance, not on scan.
- Option B: Allow one reactivation after TTL expires, with a cooling-off window (e.g., 2 hours), rate-limited per user.
- Option C: Allow reactivation freely, accept some abuse, monitor during pilot.

Option B is the most defensible for a pilot where fraud is bounded and measurable.

---

## Idea 4 — Voucher / Activation State Machine

**Status: the proposal describes states implicitly but never maps them. This is a real gap.**

The proposal mentions `issued`, `activated`, `expired`, `redeemed` in prose. But the transition rules between states are not written down anywhere. Without an explicit state machine:

- Backend developers will make different assumptions
- Edge cases (what happens when TTL fires while code is being scanned?) are undefined
- Abuse scenarios can't be analyzed systematically

Proposed state diagram:
```
issued → activated → code_generated → [pos_confirmed | ttl_expired]
       → shared → (transferred to recipient, follows same path)
       → expired (voucher lifetime ended, never activated)
```

`pos_confirmed` is a lagged batch state from partner POS data. `code_generated` is our real-time proxy.

**Recommendation:** Add an explicit state machine section to the technical proposal before development begins. This is not optional — it directly affects database schema, bot logic, and dashboard counts.

---

## Idea 5 — Backup Plan if Retail Code Pools Fail

**Status: most critical operational risk in the proposal, currently underspecified.**

The proposal says "code pools are fixed in agreement before start." But agreeing to provide code pools and actually delivering them are different things. Magnum's IT team may have their own timelines. CU may change partner terms. Glovo may restrict promo code formats.

The proposal lists fallback options but doesn't assign probability or select a primary fallback. This leaves the launch plan fragile.

**Concrete fallback tiers (recommended):**
1. **Tier 1 (preferred):** Partner delivers code pool 14+ days before launch. Standard flow.
2. **Tier 2 (delayed pool):** Partner promises codes but delays. Launch with promo-point channel only; retail added when codes arrive.
3. **Tier 3 (partner fails):** Pivot to cashback mechanic — user buys, uploads receipt, gets Kaspi refund. Requires separate KGD API integration.
4. **Tier 4 (full fallback):** Promo-point-only pilot with manual code management. Smallest viable pilot.

**Recommendation:** Define which tier triggers which response, and assign a decision date (e.g., "if code pools not confirmed by D-21, activate Tier 2").

---

## Idea 6 — Expiry Windows Tradeoff

**Status: correctly identified as a tuning question. Not a blocker, but needs to be documented.**

Current values (30-day voucher, 15-minute activation code) are reasonable for pilot. The tradeoff is real:
- Longer voucher lifetime → higher eventual activation rate, lower urgency
- Shorter TTL → lower fraud exposure, but more "I ran out of time at the register" UX failures

The 15-minute TTL is already a known UX risk for users who are slow at the register or have connectivity issues at checkout. The backup for this (pre-generated promo-point codes for offline mode) addresses only that channel.

**What's unresolved:** what happens if a user's code expires at the register because the cashier was slow? The bot will need a clear message and a path to reactivate (which loops back to Idea 3).

**Recommendation:** Keep current values for pilot, but add a specific UX flow for "code expired during checkout" — even if the resolution is just "wait 5 minutes and try again" with a rate-limit on reactivation attempts.

---

## Idea 7 — Should Cashback Be Framed as Stage 2?

**Status: yes, and it should be explicitly tied to Idea 5.**

Currently the proposal has three Stage 2 bullets (geography, partners, branding) and cashback is mentioned but not formalized.

Adding cashback as explicit Stage 2 serves two purposes:
1. It makes the pitch stronger — the platform has a clear evolution path if retail integration proves slow
2. It gives the brand a contractual fallback — if partner code pools fail, the project doesn't die, it pivots

**Recommendation:** Add cashback/receipt refund as Stage 2 in the proposal, with explicit trigger conditions from Idea 5. Frame it as "platform maturity" not "backup plan" — this is a feature, not a failure mode.

---

## Summary Assessment

| Idea | Priority | Status |
|------|----------|--------|
| 1. Cashback fallback | High | Needs trigger conditions and KZ mechanics |
| 2. Telegram identity | Medium | Needs fraud tolerance threshold defined |
| 3. Partner-lock rules | High | Blocking — must be resolved before dev |
| 4. State machine | High | Blocking — must be written before dev |
| 5. Code pool backup plan | Critical | Most likely launch risk |
| 6. Expiry windows | Low | Pilot tuning, not a blocker |
| 7. Cashback as Stage 2 | Medium | Strengthens roadmap story |

Ideas 3, 4, and 5 are the ones that will cause real problems if left unresolved before development starts.
