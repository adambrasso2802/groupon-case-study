# Phase 3 — Adversarial pass on the Part 1 draft

I am the toughest reviewer in the room. Here is where the current draft is weakest.

## 1. The principle is good. The deprioritization is good but under-defended.

"Activate, don't notify" survives the cross-deal-type test. The deprioritization of short-term refund volume is the kind of call a senior PM should make and most candidates won't. **But** the draft asserts this trade is worth it without quantifying the exposure. A reviewer will ask: "How much refund cost are you actually willing to absorb? At what point do you pull the lever?" Right now I have +2pp as a guardrail in E1 — that's good for the experiment, but the principle needs a strategic number too. Suggested fix: name a quarterly refund-cost ceiling, framed as "we will absorb up to X% lift in refund cost in service of redemption lift; beyond that we revisit." A range like 10–15% absolute lift in refund volume is defensible if the redemption rate lifts by ≥5pp.

## 2. The "Plan-it" hypothesis is the right shape but its magnitude is intuition-led.

8pp absolute is a big claim. Implementation-intentions effects in behavioral econ studies typically run 5–15pp in lab settings, lower in field. **8pp is at the upper end for a single intervention without product-side enablement.** Honest reframe: "we hypothesize a 5pp lift; we'd run E1 to ship at 3pp." That's the sandbagged version of the claim, but it's the defensible one. Calling it 8pp without a base-rate citation is a tell that I'm hoping more than projecting.

## 3. E2's eval gate is correct, but the experiment risks being a "feature test," not a learning test.

If E2 wins, what have I *learned* — that AI-generated content beats generic content, or that *deal-type-specific* content beats generic? Without an arm that isolates personalization from deal-type-awareness, E2 will conflate the two. The principled fix: run E2 as a 3-arm test — control (generic), arm A (human-templated per-deal-type), arm B (AI-generated per-deal-type-and-merchant). If A beats control and B doesn't beat A, the AI work isn't justified. Right now I'm only running B, which means I might ship AI for AI's sake.

## 4. The leading indicator definition has a leak.

"Commitment action" includes "user-set redemption-by date with reminder." That's the weakest of the three — a user clicking "remind me in 2 weeks" is closer to a snooze than a commitment. It will look good in the metric (high take-rate) but won't predict redemption. Tightening: count "remind me later" with a chosen date as a *weak commitment*, surface it separately, and don't let it become the metric's volume driver. The strong commitments (confirmed booking, calendar entry with date) should be the primary read.

## 5. Buy-Again rules: the "after positive merchant rating" gate has an operational hole.

I gate Buy Again on "confirmed redemption with positive merchant rating." But most users don't rate. If I make positive-rating a hard gate, I lose 60–80% of the eligible audience. Operational fix: gate on **"absence of negative signal"** — no refund, no support contact, no 1-2 star rating if rated. Default-on, not default-off. This is a small but real implementation detail that would otherwise quietly cut the addressable surface.

## 6. T1 (merchant reliability) is correctly out of scope, but the diagnosis section doesn't flag the feedback loop.

The fix I'm shipping (Layer 1 commitment + Layer 2 hold) will *generate signal* about merchant reliability — booking failures, no-shows surfaced earlier, refund reason codes. The diagnosis section names T1 as out of scope without noting that we'll be *building the instrumentation that lets someone else fix it later.* That's a senior framing — a 90-day plan that creates the data for the next 90-day plan. Worth a sentence.

## 7. The system description is good. The system description is also long.

Three layers, four paragraphs each → reviewer fatigue. The final submission version should compress §3 to one paragraph per layer max, ideally with a sentence-level summary up top. Concise > exhaustive, per the brief.

## 8. Missing: an explicit statement on web vs. mobile.

The JD calls out consistency across web and mobile. The draft never mentions platform. The commitment mechanic is mobile-native by default (calendar APIs, push reminders), but the strategy must hold on web for buyers who arrived there. One sentence noting this — and that mobile is the *primary* surface because of native commitment primitives — closes the gap without inventing scope.

---

## Where the draft scores well (don't change these)

- The H1/H2 split with the why-secondary reasoning is the strongest section.
- The "activate, don't notify" principle survives the test.
- The local-vs-goods leading-indicator split is the single most-differentiated call in the doc.
- The "out of scope" sentence on merchant reliability is the right kind of senior move.

---

## Suggested edits before locking Part 1

1. Quantify the refund-cost ceiling in §2.
2. Sandbag E1 magnitude to 5pp; flag 8pp as the *aspirational* ceiling.
3. Add a 3-arm structure to E2 (control / templated / AI).
4. Tighten the commitment-action definition to exclude weak-commit "remind me" clicks from the headline metric.
5. Change the Buy-Again gate from positive-rating to absence-of-negative.
6. Add one sentence in §1 (diagnosis) noting that the commitment-and-hold work *generates* merchant-reliability signal for future T1 work.
7. Add one sentence on web/mobile parity, primary surface mobile.
8. Compress §3 in the final submission version.
