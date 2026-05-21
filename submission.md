# Senior Product Manager, Post-Purchase: Case Study Submission

**Adam Brassington · May 2026**

---

## Operating principle for this submission

> AI compresses the time from question to evidence by 10x. It does not compress the time from evidence to conviction, or from conviction to alignment — and the second two are where this role's leverage actually lives.

Every section below was built that way: AI did the legwork (data triangulation, evidence synthesis, prose drafting), I made the calls. The AI Usage section at the end is specific about which tool did what.

---

# Part 1 — Redemption Clarity & Repeat Purchase Strategy

## §1. Diagnosis

**The first-purchase voucher for a local service is never converted into a planned action.** A buyer completes checkout with vague future intent ("I should get a massage sometime"), receives a receipt-framed confirmation, and is dropped back into deal-browsing. Without a commitment moment in the first 48 hours (a chosen date, a booking, a calendar hold), salience decays. By the time the user surfaces redemption intent, the context is cold, the next step feels uncertain, and the deal has to re-win attention against everything else in their life. That loop produces the case's stated >10-day median TTR for local services, the "How do I use this?" support contacts arriving *late* in the window, and the refund-on-expiry tail.

**This is the root, not a symptom** (based on the case's stated signals and triangulated against external review patterns on Trustpilot, App Store, and Reddit), because it's the only explanation that fits all four signals simultaneously: (a) declining redemption in local but not goods (goods has no "decide when" step; the package arrives), (b) a rising median TTR (intent is decaying, not just timing-out), (c) a top support driver about *use*, not *purchase* (users surface confusion when they finally try to act), and (d) refunds correlated with unredeemed-plus-unclear. A pure-clarity diagnosis would predict support contacts to spike *early*; a pure-friction diagnosis would predict a sharp redemption cliff near expiry. We see neither. We see the signature of decay.

Where I cite specific baseline numbers in this submission (~55% redemption, ~1,500 per arm, ~25%/~8% repeat-rate split between redeemers and non-redeemers), these are working assumptions I'd verify on day one and recalibrate against the actual funnel. The structure of the argument doesn't depend on the exact values.

**Secondary explanation: per-deal-type next-step ambiguity.** A generic "redeem" surface for what are really four different actions (book online, phone the merchant, pick a date on a partner site, walk in). Real and evidenced in user reviews. It's secondary because it's a *necessary enabler* of the primary fix, not load-bearing alone. A beautifully written per-deal-type help page, shipped without a commitment mechanic, moves support contacts but not repeat-purchase rate. A commitment mechanic without per-deal-type specificity can't function: you can't add a calendar hold without picking a time. They ship together; commitment is the lever, deal-type specificity is what makes the lever pullable.

**Explicitly out of scope: merchant reliability** (overbooking, no-shows, refusing to honor). Real, surfaced clearly in public reviews, contributes to refunds. Not in this strategy's first 90 days: the Post-Purchase team doesn't own merchant quality, and trying to fix it from a post-purchase seat dilutes focus. Named here so it doesn't quietly creep into scope. The commitment-and-hold work *generates* the merchant-reliability signal that lets another team act on this later.

## §2. Guiding principle

**Activate, don't notify.**

Every post-purchase touchpoint exists to advance the user toward redemption, not to inform them about what they bought. Comms that don't move the user one concrete step closer to use are not "softer engagement"; they're noise we are accountable for sending. The product's job after checkout is to do as much of the activation work *for* the user as possible (pick the date, set the reminder, surface the merchant phone with one tap), so that "having bought" and "having used" feel like the same continuous action, not two separate decisions.

This principle survives across deal types, platforms, and markets because it's about *whose work it is.* Local needs us to book the slot; goods needs us to surface the moment of arrival; gifting needs us to do the activation work for the giftee specifically. Mobile is the primary surface because of native commitment primitives (calendar, push, location); web preserves the same artifacts in a user-pull form. The principle generalises across Groupon's international markets, but specific booking-partner integrations and merchant-data completeness vary by country, which will gate sub-vertical rollout sequence. The medium changes; the principle doesn't.

**Willing to deprioritize: short-term refund volume.** A commitment mechanic surfaces redemption intent earlier, which surfaces merchant-side friction that today is hidden by the simple fact that the user never tried. Some of that friction will convert to refund requests instead of silent churn. I'll absorb up to a ~10–15% lift in refund volume in service of ≥5pp redemption lift, revisited beyond that threshold. The trade buys: (a) visible merchant-reliability signal, (b) long-term repeat-rate gain from successfully activated users, (c) elimination of silent churn, which is worse than visible refunds because it bleeds the metric we actually care about.

## §3. Redemption → Retention as a system

Three layers, each enabling the next.

**Layer 1 — Activation (first 48 hours).** The post-checkout experience asks "when will you use this?" in a deal-type-aware way: deep-link to the booking partner for restaurants; one-tap call plus calendar slot picker for wellness; calendar confirm for events; user-set "use within X" target for walk-in services. Output: a *commitment artifact* (calendar entry, booking, scheduled reminder) owned by the user, generated by us.

**Layer 2 — Hold (between commit and redemption).** A single, well-timed nudge tied to the user's commitment, not a Groupon cadence. Booked a slot → nudge 24h before. Set "use within two weeks" → nudge 48h before their deadline. Neither → one fallback nudge at day 7, framed as a re-entry into Layer 1. Nudges fire against user-set context, never blast cadence. This is how we reduce TTR without pressure: moving the decision into the moment of highest intent, not adding reminders.

**Layer 3 — Repeat (post-redemption only).** "Buy Again" prompts surface only when **(no refund) AND (no purchase-tagged negative support contact) AND (no 1–2 star rating if rated)**. Gate on absence of negative signal, not presence of positive: most users don't rate. Surface in the deal-type-relevant category, within the recall window (7 days for local, immediately after delivery for goods, 24h after the event). Must not surface: before redemption (dilutes commitment); after refund or no-show (insulting); inside mid-task flows on another deal; to giftees who haven't yet redeemed (turns gifting into acquisition and damages trust on both sides). **Buy Again is earned by a positive experience, not triggered by a successful transaction.**

## §4. Experiments — two for the first 60 days

### E1. "Plan-it" — commitment mechanic at post-checkout (local services)

- **Hypothesis.** Local-services first-purchase buyers offered a deal-type-aware "plan when you'll use this" action immediately post-checkout will reach a 30-day redemption rate **5pp higher absolute** than control (expected; ship at 3pp; aspirational ceiling 8pp). Magnitude pre-registered against actual baseline once read on day 1; see sensitivity table below.
- **Primary metric.** 30-day redemption rate, local-services first-purchase cohort.
- **Guardrail.** Refund request rate within 30 days, same cohort. Stop condition: +2pp absolute.
- **Secondary read-outs.** Median TTR (expect material compression), "How do I use this?" contact rate (expect decrease), commitment-action take-rate (the leading indicator).
- **What I'd need to believe.** That commitment-at-checkout shifts behavior, not just clicks (implementation-intentions literature supports this; verify in our product). That we have merchant metadata to make the deal-type CTA accurate at scale. If merchant data is incomplete in a sub-vertical, ship there only when ready, explicitly defer rest.
- **Sample-size sanity.** Baseline ~55% → ~1,500 per arm at 5pp MDE / 80% power. <1 week of exposure at Groupon weekly local cohort scale.

| If actual baseline is | Expect | Ship at | Ceiling |
|---|---|---|---|
| ~35% (high headroom) | 6–10pp | 4pp | 12pp |
| ~50% (mid) | 4–7pp | 3pp | 9pp |
| ~65% (ceiling risk) | 2–4pp | 2pp | 6pp |

### E2. AI-generated "what happens next" — deal-type and merchant-aware (post-purchase comms)

Three-arm design so a win is informative, not just positive.

- **Hypothesis.** AI-generated, deal-type-and-merchant-specific post-purchase content lifts 7-day redemption rate **4pp absolute vs. control**, by collapsing the cognitive cost of identifying the right first action.
- **Arms.** A: generic confirmation (control). B: human-templated per-deal-type content (no LLM). C: AI-generated per-deal-type-and-merchant content.
- **Primary comparison.** C vs A (does the intervention beat status quo?).
- **Secondary, more informative comparison.** C vs B (does AI personalization beat a well-written template?). If C ≈ B and both beat A, the win is "deal-type content matters" and we ship the template; AI is not justified on this surface. If C > B, AI is justified and scales.
- **Primary metric.** 7-day redemption rate, local cohort.
- **Guardrail.** "How do I use this?" support-contact rate within 7 days. Stop condition: any increase. (If our AI creates confusion, we ship it back.)
- **Pre-launch quality gate.** Eval set of 200 deals across local sub-categories; human review on accuracy of merchant-contact fields (phone, booking URL, address, redemption type). Block launch on any hallucination of merchant-contact data. This is a production AI feature, not a research demo.
- **What I'd need to believe.** That merchant metadata is complete enough across critical sub-verticals to populate the next-step. If 30%+ of records are missing critical fields, AI degrades to generic and we ship something worse than the existing confirmation. Audit completeness *before* running.
- **Sample-size sanity.** Baseline ~30% (7-day rate is lower than 30-day) → ~2,200 per arm × 3 arms = ~6,600 total. Run-time comparable to a two-arm test at Groupon scale.

**Run order.** E1 first: the mechanism is higher-confidence and the result informs E2's prompt template. E2 layered after E1 reads out, measuring incremental lift over the commitment mechanic, not against an untreated baseline.

## §5. Key metrics

**Outcome metrics.**
1. 30-day local-services redemption rate (primary outcome of redemption-clarity work).
2. 1st → 2nd purchase rate in 90 days, local cohort (primary outcome of retention work).
3. Refund request rate, local cohort (guardrail with defined tolerance, see §2).

**Leading indicator.** **% of first-purchase buyers who take a *strong* commitment action within 48 hours of purchase.** A strong commitment is *narrowly* defined: a confirmed merchant booking, or a calendar entry with date from our flow. "Remind me later" with a chosen date is a *weak* commitment, tracked separately, never the headline metric. (Weak commitments are closer to a snooze than a commitment, and counting them inflates the indicator without predicting redemption.) The strong-commitment rate reads ~1–2 weeks before redemption-rate movement and ~6 weeks before repeat-rate movement.

**How this reads differently for local vs. goods.** For local, the commitment-action rate is the *cause.* A rising rate predicts redemption ~1–2 weeks out and repeat ~6 weeks out. If commitment-action rises and redemption doesn't follow, we're collecting clicks, not behavior; sharpen Layer 2 before adding new Layer 1 surfaces. For goods, the commitment-action rate is a *confound*, not an indicator. Goods has no booking, no date to pick: the package arrives when it arrives. The equivalent for goods is **% of buyers who return to a Groupon surface within 7 days of delivery.** Goods buyers don't need to be activated *into* redemption (delivery does that); they need to be activated *back to the marketplace* in the moment they feel positive about the brand. **In one line: for local we measure whether the user committed; for goods we measure whether the user returned.** Any team using one indicator for both deal types is reading goods through a local lens.

---

# Part 2 — Gifting Experience & Giftee Activation

## §1. The Giftee Moment

**The highest-leverage moment is the giftee landing: the first time the recipient is in our product.** Earlier stages either don't move activation (gift purchase) or aren't product-leverage problems (delivery is a channel-and-deliverability problem). Later stages either inherit Part 1's work (redemption) or are gated on something that hasn't happened yet (giftee → customer).

**Current state.** The giftee taps an email or SMS link and lands on a page that looks like a deal page with a "claim" CTA. Many flows gate sign-in or account creation before the gift is fully visible. The giver's note sits in a quote-box; there's no merchant context, no warmth, no next-step. A brand-new visitor, who didn't choose this deal, is treated as an existing customer with a transaction to manage.

**What breaks.**
1. **Cold start.** Giftee didn't pick the deal, may not know Groupon.
2. **Friction before value.** Sign-in gates before the gift is seen.
3. **Lost relational context.** The giver's note is the warmest signal in the journey; the current page demotes it.
4. **No commitment hook.** Same H2 problem as direct purchase, worse because the giftee has even less context.
5. **No bridge to repeat.** First impression is "figure this out yourself."

**Redesigned experience: "The Welcome."** A single-screen, AI-personalized giftee landing built on five moves:
1. **Name what they got in human terms.** "A 60-minute deep-tissue massage at Bliss Spa in Wicker Park, on Sarah", not "Voucher #12345."
2. **Frame the giver.** The note is the headline, not a sidebar. If no note, AI generates a warm, deal-type-aware default.
3. **Set the scene.** AI-generated short paragraph using merchant metadata: what the experience is, what's included, what to expect on arrival. Never invents merchant facts.
4. **Offer the commitment moment.** Same Layer-1 mechanic from Part 1 (deal-type-aware "Book now / Set reminder / Save for later"), sized for a first-time Groupon user.
5. **Defer the account.** Identity is implicit (tied to the gifted email/phone). No credentials until booking or redemption.

**This is the same commitment primitive from Part 1, deployed in the highest-leverage cold-start moment in the product.** No new infrastructure beyond the AI-generation layer that E2 already justifies. Giftee → customer conversion isn't a separate workstream: it's the downstream of a Welcome that earns trust on first contact.

## §2. Purchaser Confidence

**Improvement: a "see what they'll see" preview at gift purchase, plus a *Delivered → Welcomed* timeline.**

Purchaser anxiety has a specific shape: *did it land, did it land well, will they use it.* Today the purchaser sees a "sent" confirmation, then nothing. Two pieces close the gap:
1. **At purchase:** an exact preview of the Welcome the giftee will receive, with the giver's note rendered live. The purchaser tunes the note in context, watches it land, and confirms the experience.
2. **After delivery:** a two-state timeline, *Delivered → Welcomed.* The signal the purchaser actually needs (it landed, it was met with a real Welcome) without crossing into surveillance of what the giftee did next. A "Planned" state would be informative but leaks more than a cautious giftee would accept; privacy beats marginal purchaser reassurance.

**Connection to the giftee redesign.** This works *only because* the giftee experience now has a Welcome worth previewing: the purchaser's preview is the same artifact the giftee will see. Same product feature, two sides. Repeat gifting follows directly: the purchaser who sees their gift land well is the most likely person to gift again.

## §3. AI-Enabled Prototype

See `prototype.html` and the production spec in `prototype_spec.md`. A live version of the same concept is also at `https://giftee-landing-demo.lovable.app/`.

The prototype demonstrates **"The Welcome"** for three gift types (a birthday spa, an anniversary dinner, a graduation experience), each rendered with AI-personalized framing, merchant context, and a deal-type-aware commitment CTA. The annotation panel calls out what is AI-driven, what data feeds it, and the production prompt schema. The three examples are pre-generated to demonstrate the personalization is real (different tone, different next-step, different merchant context per deal type) rather than a single template with field substitution. The HTML prototype carries the production-spec annotations; the Lovable build is the same concept rendered as a polished React app for quick browser viewing.

---

# Part 3 — Prioritization, Sequencing, and What Would Change My Mind

## §1. What ships in the next 60–90 days

Sequenced against the JD's 30 / 60 / 90 milestones. Every workstream traces back to H1 (commitment) or its enabler H2 (deal-type specificity). Nothing else ships in this window.

**Days 1–14: Baseline & instrumentation.** Lock the numbers the strategy depends on: actual 30-day local-services redemption rate by sub-category; time-to-redemption distribution shape (long tail or hard cliff?); refund attribution (merchant-side vs customer-side, by reason code); merchant metadata completeness audit (gate for E2 and the Welcome); commitment-action event taxonomy instrumented. *Output: the JD's Day-30 funnel audit and "top three levers."* Contingency: if refund attribution returns predominantly merchant-side (≥80%), H1 is not the right primary lever and the plan pivots upstream to merchant-quality coordination before redemption work scales.

**Days 15–35: E1 build and launch ("Plan-it").** Single-market, single-sub-category start, in health & wellness where TTR is worst. **This is a deliberate inversion of the usual "pilot in your strongest sub-category" instinct: clean signal-to-noise matters more than ceiling, and if the mechanic fails it should fail where users are already underserved, not where they're paying full attention.** Three deal-modality variants (booking partner / phone / walk-in). E1 magnitude locked against actual baseline. *JD's Day-60 milestone: first AI-driven or A/B experiment live.* Leading indicator starts reading by week 5.

**Days 35–60: E2 build in parallel.** AI prompt scaffold, fallback templates (Arm B, shippable on its own), eval-set construction (200 deals), human-review loop. Merchant metadata gap-filling for top ~100 in-scope merchants. E2 cannot launch without the eval pipeline.

**Days 60–75: E1 readout, E2 launch.** E1 wins, partially wins, or doesn't; roll to remaining sub-categories or pivot. E2 enters three-arm experiment against the post-E1 baseline.

**Days 75–90: Giftee Welcome controlled rollout, Q5–Q6 roadmap.** The Welcome reuses E2's AI primitive; it cannot precede it. Launches to a controlled slice of gifted purchases in sub-categories where E1 and E2 already ship. *JD's Day-90 milestone: first experiment results in, two-quarter roadmap drafted with AI features as primary lever.*

**Three priorities in plain English.** Get the baseline. Ship the commitment mechanic. Ship the AI primitive (E2) and reuse it for giftees.

## §2. What I would explicitly NOT pursue yet

**A cross-deal-type loyalty / rewards program**, even though it would lift repeat-purchase rate measurably in the short term.

Loyalty on a broken redemption funnel rewards the wrong behavior and masks the signal we need to read: it pays users for purchasing rather than for using, inflating repeat-rate cosmetically while H1 stays unaddressed. Revisit the quarter after E1 and E2 read out positive. Loyalty amplifies a working system; it papers over a broken one.

(Merchant-quality / T1 is also deferred, but for a different reason: not in this team's lane. Loyalty is the harder call because it *is* in our lane and the commercial pull is real.)

## §3. What would change my mind

**Load-bearing assumption: that redemption is causally upstream of repeat purchase, not just correlated with it.**

The leadership hypothesis says "customers who redeem successfully are significantly more likely to purchase again." That's a correlation. The whole strategy assumes the causal arrow runs redemption → repeat. If it runs the other way — engaged users redeem *and* repeat because they're engaged, not because the redemption caused the repeat — then moving redemption rate won't move repeat rate, and the 90-day plan is solving an interesting problem that doesn't matter commercially.

**Falsifier.** In E1, the commitment mechanic moves the 30-day local redemption rate by 3pp+ but the 90-day 1st→2nd repeat rate of that same cohort doesn't follow ~6 weeks later. Lifting redemption without lifting repeat means the hypothesis is mis-specified.

**Detection.** Outcome metrics resolve ~4–5 months in. Sharper early read via 14-day post-redemption return rate and second-purchase intent in app sessions — those trend by day 75–90 if the causal claim holds.

**Pivot if falsified.** Redemption work still ships (refund / support / CSAT value stands alone) but stops being the retention lever. Roadmap moves upstream — deal-fit at purchase, browsing-to-buying confidence — depending on which sub-finding came with the falsification.

**Secondary assumption.** That commitment clicks equal commitment behavior. If take-rate is high but conversion to redemption is low, we'd need to distinguish "mechanism is wrong" from "intent was weak." Cohort segmentation by purchase context (impulse-discovery vs. searched-and-found) is the tell.

---

# AI Usage

Used per the operating principle: AI compressed the time from question to evidence by ~10x, but every call (diagnosis, deprioritization, sequencing, deferral) is mine.

**Claude (this conversation).** Did the legwork: extracted the brief, ran six parallel web searches to triangulate Trustpilot / App Store / Reddit / earnings-call signal on Groupon's post-purchase reality (Q3 2025 actives, N.A. Local billings growth, merchant-side complaint patterns), surfaced industry redemption benchmarks (gift cards, daily-deal promos) for context against the case's stated >10-day TTR. Then built and pressure-tested the diagnosis: drafted three candidate root-cause hypotheses (salience decay, per-deal-type ambiguity, confirmation-as-receipt), steel-manned each against the others, and named what would falsify each. Drafted prose, ran an adversarial pass against its own work (8 issues found, e.g. E1's 8pp magnitude was intuition-led; E2 as-written couldn't isolate AI lift from template lift; Buy-Again positive-rating gate would lose 60–80% of audience), and I accepted, edited, or rejected each before assembly. Built the prototype HTML as a single self-contained file with three pre-generated examples and an annotation teardown panel.

**Lovable.** Used to build a polished React rendering of the Welcome concept (linked above) for quick reviewer access. The HTML prototype and the Lovable build are complementary: the HTML carries the production-spec annotation depth; the Lovable build offers visual feel.

**What AI did *not* do.** Pick the root cause (T2 with T3 reframe; my call after the three were laid out). Pick the deprioritization (short-term refund volume in the principle; loyalty program in §2). Decide the experiment structure: the three-arm E2, the sandbagged E1 magnitudes, and the absence-of-negative Buy-Again gate were all edits I made on the AI's first draft. Name the load-bearing assumption (the leadership hypothesis itself is the answer; AI tried to point at the commitment-mechanism assumption first, which is the easier target).

The work is shaped by AI; the conviction is mine.

---

# Self-evaluation against the brief's criteria

Honest 1–5 against the evaluation criteria, with the weakest link flagged.

| Criterion | Rating | Why |
|---|---|---|
| Diagnosing with data signals + behavioral reasoning | **4.5** | The H1/H2 split with the why-secondary reasoning is defensible. The four-signal triangulation (declining redemption only in local, rising TTR, late support contacts, expiry-driven refund tail) is genuine behavioral reasoning. **Weakness:** I made stated working assumptions on the metrics tree (~55% baseline, ~25% redeemer repeat, ~8% non-redeemer repeat), explicitly disclosed in §1. Defensible but unverified. |
| Judgment on what to prioritize, defer, and why | **4.5** | The loyalty deferral is a real senior call: commercially attractive, in-lane, deliberately deferred for sequencing reasons. The "activate, don't notify" deprioritization of refund volume is the kind of trade most candidates won't name. The "worst sub-category first" inversion is the one sequencing call worth surfacing. |
| Comfort with ambiguity, explicit assumptions | **4.0** | Assumptions named throughout (baseline ranges, refund tolerance, what falsifies the plan). **Weakness:** I assumed the case's 55% redemption baseline rather than naming a wider range; in practice I'd want a five-point sensitivity. |
| Understanding how retention, trust, and revenue interact | **4.5** | Retention is treated as a function of trust (the Buy-Again gating logic, the giftee Welcome's deferred-account move), not just metric optimization. The deprioritization of refund volume *for* retention is the cleanest expression of this. |
| Clarity and structured thinking | **4.0** | The local-vs-goods leading-indicator distinction is the single sharpest call. The three-layer system is structured cleanly. |

**Weakest link: the metrics-tree assumptions in the diagnosis section.** They're load-bearing for the size-of-prize claim but rest on stated guesses, not data access. Honest disclosure that this is a Day-1 dependency for the actual job is the right move; pretending the numbers are verified would be worse.

**Strongest section: §3 of Part 3.** Questioning the leadership hypothesis itself, naming the falsifier, naming the pivot. That's the senior-PM move the brief is testing for.
