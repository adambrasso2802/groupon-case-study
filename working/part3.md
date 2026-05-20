# Phase 5 — Part 3 (drafted)

---

## §1. Prioritization & sequencing — what ships in the next 60–90 days

Sequenced against the JD's 30 / 60 / 90 milestones, and against the diagnosis. Every workstream below traces back to H1 (commitment) or its enabler H2 (deal-type specificity). Nothing else ships in this window.

**Days 1–14 — Baseline & instrumentation.** Lock the numbers the strategy depends on. (a) Actual 30-day local-services redemption rate by sub-category. (b) Time-to-redemption distribution shape — is it a long tail or a hard cliff near expiry? (c) Refund attribution: merchant-side vs. customer-side, by reason code. (d) Merchant metadata completeness audit (gate for both E2 and the giftee Welcome). (e) Commitment-action event taxonomy instrumented. *Output: the Day-30 funnel audit and the named "top three levers" from the JD.*

**Days 15–35 — E1 build and launch ("Plan-it" commitment mechanic).** Single-market, single-sub-category start — health & wellness, where TTR is worst. **Worst sub-category first is the deliberate call: highest headroom (cleanest signal-to-noise on the lift), and if the mechanic is wrong it breaks where users are already least well-served, not where they're paying full attention.** Three deal-modality variants (booking partner / phone / walk-in). E1 magnitude locked against actual baseline from days 1–14. *This is the JD's "first AI-driven or A/B experiment live" Day-60 milestone — and the leading indicator (commitment-action rate) starts reading by week 5.*

**Days 35–60 — E2 build in parallel, eval pipeline, three-arm setup.** AI prompt scaffold, fallback templates (Arm B — already shippable on its own), eval-set construction (200 deals across sub-categories), human-review loop. Merchant metadata gap-filling for top ~100 merchants in scope. E2 cannot launch without the eval pipeline; no shortcut on this.

**Days 60–75 — E1 readout, E2 launch.** E1 wins, partially wins, or doesn't — and we either roll out to remaining local sub-categories or pivot. E2 enters three-arm experiment phase against either control (if E1 didn't ship) or post-E1 baseline (if it did).

**Days 75–90 — Giftee Welcome controlled rollout, Q5-Q6 roadmap.** The Welcome reuses E2's AI generation primitive; it cannot precede it. Launches to a controlled slice of gifted purchases in the sub-categories where E1 and E2 have already shipped. *This is the JD's Day-90 milestone: first experiment results in, roadmap for next two quarters drafted with AI features as the primary lever.*

**Three priorities in plain English.** Get the baseline. Ship the commitment mechanic. Ship the AI primitive (E2) and reuse it for giftees.

---

## §2. What I would explicitly NOT pursue yet

**A cross-deal-type loyalty / rewards program** — even though it would lift repeat-purchase rate measurably in the short term.

Loyalty on a broken redemption funnel rewards the wrong behavior and masks the signal we need to read: it pays users for purchasing rather than for using, inflating repeat-rate cosmetically while H1 stays unaddressed. Revisit the quarter after E1 and E2 read out positive — loyalty amplifies a working system; it papers over a broken one.

(Merchant-quality / T1 is also deferred, but for a different reason — not in this team's lane. Loyalty is the harder call because it *is* in our lane and the commercial pull is real.)

---

## §3. What would change my mind

**Load-bearing assumption: that redemption is causally upstream of repeat purchase, not just correlated with it.**

The leadership hypothesis says "customers who redeem successfully are significantly more likely to purchase again." That's a correlation. The whole strategy assumes the causal arrow runs redemption → repeat. If it actually runs the other way — engaged users redeem *and* repeat because they're engaged, not because the redemption itself caused the repeat — then moving redemption rate won't move repeat rate, and the entire 90-day plan is solving an interesting problem that doesn't matter commercially.

**The signal that would falsify it:** in E1, if the commitment mechanic moves the 30-day local redemption rate by 3pp+ but the 1st→2nd 90-day repeat rate of that same cohort doesn't follow ~6 weeks later, the causal claim is suspect. We'd be lifting redemption without lifting retention — which means the leadership hypothesis is mis-specified and the diagnosis section was solving the wrong problem.

**How early I could detect it:** E1 reads out around day 50–60 on redemption. The 90-day repeat read on the same cohort lands around day 110–140. So the falsification window is **roughly 4–5 months from the start of the engagement** — slow, but earlier than waiting for outcome metrics on the full strategy. We can also pull a sharper read sooner by looking at *early repeat signals* — site-return rate within 14 days of redemption, second-purchase intent surfaced in app sessions — which would trend by day 75–90 if the causal claim holds.

**What I'd do if it falsifies:** pivot. The redemption work would still ship (it has standalone value — refund reduction, support contact reduction, CSAT) but it would no longer be the load-bearing lever for retention. The next quarter's roadmap would move to upstream interventions — deal-fit at purchase, browsing-to-buying confidence, or post-redemption *quality of experience* nudges — depending on which sub-finding came with the falsification.

**Secondary assumption worth naming.** That users' weak follow-through on commitment actions (if the commitment-take-rate is high but conversion to redemption is low) means the *mechanism is wrong*, not the *intent is missing*. If we see clicks-without-follow-through, we'd need to distinguish between "the commitment isn't binding because we asked for it the wrong way" (fixable) and "the underlying purchase intent was weak from the start" (a different team's problem). The cleanest tell: cohort segmentation by purchase context — impulse-discovery buyers vs. searched-and-found buyers — should show different commitment-to-redemption conversion rates if intent is the real variable.
