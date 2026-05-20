# Phase 1 — Evidence Brief

## A. What the case tells us (knowns)

| Signal | Direction | What it implies |
|---|---|---|
| Overall redemption: flat, varies by deal type | — | Aggregate hides the local-services bleed |
| Local services redemption: declining, lowest | ↓ | Primary problem surface |
| Time-to-redemption (local): median **>10 days** | ↑ | Long latency = forgotten purchase = refund risk |
| Support contacts: "How do I use this?" is top driver | ↑ | Clarity gap is real and self-reported |
| Refund requests (local): rising; correlated with unredeemed + unclear instructions | ↑ | Friction is converting to revenue loss, not just NPS |
| 1st → 2nd conversion: lower for local-only buyers | ↓ | Local is also the retention bottleneck |
| 90-day repeat: goods > local | — | Goods buyers redeem on arrival; local buyers must self-activate |
| Leadership hypothesis | — | "Close the redemption gap or retention won't move" — this is the bet they want us to either ratify or refute |

## B. What the case does NOT tell us (gaps that matter)

1. **Refund attribution** — How much refund volume is merchant-side (no-show, overbook, refusal to honor) vs. customer-side (confusion, change of mind)? Different root cause → different fix.
2. **Redemption tail shape** — Is the >10-day median a long tail, or is the bulk genuinely late? A bimodal distribution (some redeem in week 1, many in week 8+) means two different user states, not one.
3. **Merchant booking-flow fall-through** — How many redemption attempts start in-app then end on a phone call to the merchant? That's invisible redemption intent.
4. **Giftee activation rate, absolute number** — "Significantly lower than direct" — by how much? 30 pts? 5 pts?
5. **Cohort economics** — LTV delta between a redeemer and non-redeemer of the same first deal. The leadership hypothesis is testable; we don't yet have the number.
6. **Refund cost per dollar of GMV** in local — to size the prize.

---

## C. External evidence (corroborating + new)

### Corroborates the case
- **Trustpilot (67k+ reviews, ~4.0/5)** and **App Comrade**: "voucher-redemption layer is where complaints stack up." Booking via in-app calendar fails often; experienced users default to phoning the merchant. ⟶ The "How do I use this?" support contact isn't a documentation problem alone; the flow itself breaks.
- **Industry benchmark**: gift cards see ~90% of redemptions within 1 month; daily-deal promos typically 30–40% redemption. Groupon's local median >10 days is high-friction for what should be a same-week purchase intent.
- **Q3 2025 earnings (Senkypl)**: 16.1M active customers (+4% YoY — slow), N.A. Local billings +18%, Goods explicitly de-emphasized, narrative is "marketplace transformation." Strategically: **the company is betting on Local; Local is also where the funnel leaks. The case is asking us to fix the very bet.**

### NEW evidence that reframes the case
1. **Merchant reliability is a hidden root cause.** Public reviews show: vouchers marked "redeemed" when they weren't; merchants overbook salons and turn customers away; merchants cancel appointments after booking. The case frames the gap as a *clarity* problem. The market frames it as a *trust* problem. These look the same in CSAT but require different fixes.
2. **Support is being downgraded.** Multiple late-2025 reviews flag "AI chat only, no phone support" as the reason a small confusion becomes a refund. The post-purchase journey has lost its safety net — which makes upstream clarity more load-bearing than it would otherwise be.
3. **Booking abandonment is invisible.** When users leave the in-app booking flow to call the merchant, Groupon's funnel shows a redemption gap, but the user already self-served around it. Some "low redemption" may be silently redeemed, just untracked.
4. **Active-customer growth is slow (+4% YoY).** Acquisition isn't pulling its weight; *every point of repeat-rate lift is disproportionately valuable*. The leadership hypothesis has commercial teeth.
5. **Gifting has a structural asymmetry**: gift card industry data shows redeemed gifts mostly redeem within 30 days. If giftee activation is "significantly lower than direct," that's not a long-tail problem — it's an early-window decision problem (the first 48 hours after delivery decide most of it).

---

## D. Three themes worth pulling on

| Theme | One-line case |
|---|---|
| **T1. Local-services redemption is a *trust* failure as much as a *clarity* failure** | The user doesn't trust the next step (will the merchant honor it? will booking work?). Comms alone won't close it. |
| **T2. The first 48 hours post-purchase carry disproportionate weight** | For both direct local buyers and giftees, the decision to engage is made in a window the current product treats as just "send the receipt." |
| **T3. Goods buyers are the wrong benchmark** | The case implicitly contrasts goods (high repeat) with local (low repeat) — but the goods funnel does the redemption work *for* the user (shipping). The repeat-rate gap isn't a customer-quality gap; it's a *product-completion* gap. Fix completion, the repeat-rate gap closes. |

---

## E. So what?

- The leadership hypothesis ("close the redemption gap → retention follows") is **directionally right but mis-specified.** It treats redemption as a single funnel; the data and reviews say it's at least two journeys (local vs. goods) and at least two failure modes (clarity vs. merchant-trust).
- The strongest **AI leverage point** is the first 48-hour window post-purchase for local services: personalized "what happens next" with deal-type and merchant context. This is the area where automation can shrink time-to-redemption without being pushy, and where giftee activation can be unlocked with the same primitive.
- The most likely **wrong answer** is "build a better redemption FAQ / static comms refresh." It will move support contacts; it will not move repeat purchase.

---

## Checkpoint 1

**Does anything here surprise you, and which thread do you want to pull hardest in the diagnosis?**

Suggested options to react to:
- **T1 (trust, not clarity)** — risk: pulls scope into merchant-quality work that the post-purchase PM doesn't fully own.
- **T2 (the 48-hour window)** — cleanest AI hook, cleanest experiment surface; risk of being too narrow if the real problem is structural.
- **T3 (goods is a misleading benchmark)** — most contrarian; reframes the leadership hypothesis. Highest-upside, highest-risk-of-pushback.

My recommendation if you want me to push you: **T2 as the primary**, with T1 named explicitly as a constraint we're choosing not to solve in the first 90 days. T3 belongs in the framing of the diagnosis but not as the headline.

Sources used:
- [Trustpilot — Groupon.com](https://www.trustpilot.com/review/www.groupon.com)
- [App Comrade — Groupon Local Deals review](https://appcomrade.com/apple/groupon-local-deals-near-me-352683833/)
- [Groupon Q3 2025 8-K](https://www.sec.gov/Archives/edgar/data/0001490281/000162828025050198/a2025q38-kxexhibit991.htm)
- [Yotpo — Redemption rate benchmarks](https://www.yotpo.com/blog/redemption-rate/)
- [Recurly — Gift card time-to-redemption](https://recurly.com/blog//gift-cards-time-to-redemption-makes-the-difference/)
- [DemandSage — Coupon stats 2026](https://www.demandsage.com/coupon-statistics/)
- [ConsumerAffairs — Groupon reviews](https://www.consumeraffairs.com/online/groupon.html)
