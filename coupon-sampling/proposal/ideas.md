# Open Ideas / Unresolved Options

This file contains only ideas that are **not yet fully implemented** in
`proposal/project_proposal.md`.

Implemented ideas were removed:

- Telegram as the main platform
- activation as the real-time accounting event
- promo-point anti-theft flow with promoter scan
- partner-specific code issuance at activation
- code expiry / TTL logic
- partner-locked activation flow

---

## 1. Refund / Cashback Fallback Instead of Sampling

Alternative mechanic:

- user buys product first
- uploads receipt in Telegram bot
- receipt is validated
- user receives refund / cashback

Questions:

- who validates the receipt: us, retailer, or third-party OCR / receipt engine?
- how do we pay refund in Kazakhstan: Kaspi, bank card, wallet, coupon?
- does this require retailer confirmation or can it work without retailer approval?
- for which cases should this be used:
  - fallback if code pools are delayed?
  - fallback for cities without partner activation?
  - separate mechanic for delivery or hard-to-operate categories?

Why this remains interesting:

- could reduce dependence on partner code pools
- could work as backup if retail integration is weak
- may be useful for categories or geographies where direct redemption is fragile

---

## 2. Is Telegram Identity Enough?

Current proposal assumes Telegram is sufficient for pilot identity and abuse
control.

Open question:

- is `1 Telegram account = 1 user` strong enough for Coca-Cola and partners?

Possible options:

- keep Telegram-only identity for pilot
- optionally request contact share in bot
- add stronger anti-abuse checks only if fraud appears materially in pilot

Tradeoff:

- more verification reduces abuse
- more verification increases friction and lowers conversion

---

## 3. Explicit Partner-Lock Rule Needs Better Specification

The current proposal effectively uses partner lock at activation:

- user activates
- selects partner
- receives partner-specific code

What still needs to be written more clearly:

- can user cancel before code is issued?
- can user re-activate with a different partner if the first code expires unused?
- if user selects Glovo and then goes to Magnum, what exactly happens in system terms?
- do we allow one activation attempt per voucher, or multiple activation attempts until first successful redemption?

This is not an unresolved concept, but it is still an unresolved **rules
specification**.

---

## 4. Voucher / Activation State Model

The proposal describes the logic, but does not yet define the state machine
explicitly.

It would be useful to formalize:

- `issued`
- `shared`
- `transferred`
- `activated`
- `expired`
- `redeemed`
- `cancelled` or `activation_expired`

Why this matters:

- avoids ambiguity in product logic
- simplifies backend design
- makes abuse scenarios easier to reason about
- helps explain the mechanic to partners

---

## 5. Backup Plan if Retail Code Pools Fail

Current proposal assumes partner code pools will be available before launch.

Open question:

- what happens if Magnum / CU / Glovo delay code pool delivery or change conditions?

Possible fallback options:

- cashback / refund mechanic
- promo-point-only pilot
- limited launch with only one partner first
- temporary internal code system where operationally possible

This should likely be addressed explicitly, because code-pool dependence is one of
the biggest launch risks.

---

## 6. More Explicit Tradeoff on Expiry Windows

The proposal already chose:

- voucher lifetime
- activation-code TTL

But the tradeoff is still worth preserving here as a product question:

- longer lifetime improves convenience and activation probability
- shorter lifetime improves anti-fraud and urgency

The current values may be correct for pilot, but might need tuning after first
campaign data.

---

## 7. Should “Refund / Cashback” Be Framed as Stage 2?

The proposal currently develops:

- retail redemption
- delivery redemption
- promo-point redemption

Open product question:

- should refund / cashback be framed as a formal next-stage extension?

Reason:

- it would strengthen the story that the platform can evolve if partner
  operations prove too slow or too rigid

This may be worth adding not as pilot scope, but as roadmap logic.
