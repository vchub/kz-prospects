Add pure refund option instead of sampling:

- user buys product
- scans and upload receipt in telegram bot
- we send receipt #, to retail partner to confirm it's valid
- if valid refund user (how? kaspi?)

---

Jenya (edit) mentioned that there is problem of sampling theft.
Solution idea.

On mobile station there is telegram/qr code/link to download promo qr code.
User downloads it and show it to a promoter.
A promoter scans the code and give a sample to a person.

So we can account for given samples through the codes - associate verified (if it's telegram platform) people w/ codes, and samples distribution.

---

analysis of Mechanic:

- No OTP/verification step after phone number entry — risk of fake numbers
  inflating coupon issuance
- "Choose a retail partner" — what happens if the user selects Glovo but then
  visits Magnum? Is the coupon partner-locked?
- Coupon expiry window not defined — critical for conversion rate and abuse
  prevention

idea:

- we use telegram as platform - no need for phone and user verification
- we don't need separate mobile or web app w/ account, etc
- a user activate coupon by selecting a retail partner - coupons/codes are issued by retail partners or by us for mobile promo points.
- activation is the way to account for the moment of sale/code redemption - we want to see live statistics while pos data from retail partners will be a lagged batch transfer

---

note:
Coupon activation is important point - we want it's activated in moment or before redemption on pos, but in retail we'll not be able to get pos data online, only w/ lag and in batch.
So we want to fix/account this moment somehow.

---

Coupon/code expiration - open question - what are pros and cons?

---

Option A — Locked to selected partner at activation:

- User activates → picks Magnum → gets Magnum-specific barcode → can only redeem
  at Magnum
- Pros: retail partner gets exclusive attribution, cleaner traffic measurement,
  easier partner negotiations ("we drive traffic specifically to you")
- Cons: user friction if they change their mind; if Magnum is closed, coupon is
  stuck

What if we a user get a confirmation that they will get the coupon, but the coupon will be issued when a user request it - when he approaching the pos of retail or promo point?
