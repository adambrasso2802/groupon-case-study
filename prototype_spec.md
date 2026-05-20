# The Welcome — Prototype Spec

Reproducible spec for the giftee landing experience. The HTML prototype demonstrates this; this doc is what I'd hand to engineering and design to build it in production.

---

## 1. What this is

A single-screen, AI-personalized giftee landing page that replaces the current generic gift-redemption page. The same primitive supports a "preview" mode used by the purchaser at gift purchase (closing the Part 2 §2 confidence gap with the same artifact).

## 2. Why this surface

- Giftee landing is the highest-leverage moment in the gifting funnel — the only stage where the recipient is in our product, with intent we can convert.
- It's a cold-start: the giftee didn't choose the deal, may not know Groupon, has zero history.
- The same Layer-1 commitment mechanic from Part 1 deploys cleanly here. We are not building a new behavior, we are extending an existing one to the giftee's first 48 hours.

## 3. Components

| Component | Type | Notes |
|---|---|---|
| Hero (deal-card framing) | Rendered | Banner with deal title in human terms + giver name + occasion ribbon |
| Note card | Rendered | Giver's note as the headline, not a sidebar. Falls back to a generated default if no note. |
| Scene paragraph | AI-generated | 50–80 words of merchant context, factual only. |
| Merchant card | Rendered | Pulled from existing merchant metadata. |
| CTA prompt | AI-generated | One sentence calibrated to the deal type's typical lead time. |
| Commitment action stack | Routed template | Three options: Primary (booking modality–specific), Reminder, Save. Labels parameterised. |
| Deferred-account banner | Static | Surfaces only when giftee is not signed in. |
| Footer | Static | Value, expiry, refund link. |

## 4. AI behavior — exactly what's generated

Four constrained outputs per render:

1. **hero_line** — ≤16 words. Names the giver, the experience, and one place anchor. No price, no phone, no URL.
2. **scene_paragraph** — 50–80 words. Composes factual merchant context (hours, location color, what to expect on arrival, weather/scheduling caveats). Sourced only from structured merchant fields.
3. **cta_prompt** — ≤24 words. Suggests a tone for the next action, calibrated to merchant's lead time (e.g. "book ahead — weekends fill up" vs "no rush, walk-in friendly").
4. **cta_primary_label** — ≤6 words. Tied to the merchant's booking modality (online booking / phone / walk-in / date pick).

**Not AI-generated** (intentionally): the three commitment actions themselves, the merchant data, the footer, the deferred-account banner. The model picks *which* CTA to lead with and *how* to frame the moment; it never invents the action itself.

## 5. Inputs

```yaml
giver_name: string
giver_note: string | null
giftee_first_name: string | null   # known only if address-book hint provided
deal:
  title: string
  category: enum (local.*, ttd.*, restaurant.*, event.*, goods.*)
  merchant:
    name: string
    neighborhood: string
    booking_modality: enum (online_booking_partner, phone, walk_in, date_pick, shipped)
    booking_url: string | null
    hours: object
    weather_policy: string | null     # for outdoor/experience deals
    review_count: int
    avg_rating: float
channel: enum (email, sms, link, printed)
occasion_hint: string | null         # inferred from note, optional
```

## 6. Constraints (hard guardrails)

- Never invent merchant facts not present in the input. Phone numbers, prices, URLs, hours, and named features are forbidden unless in metadata.
- Never assume the giver–giftee relationship. The note may say "Dad" or "babe" or nothing; the model never extrapolates.
- If the giver's note is empty, generate a neutral, deal-type-aware default. Never silence-fill with relational language.
- Tone is calibrated to the giver's note tone. The note is a *hint*, not a copy target — we never echo the note's phrasing.
- If any required merchant field is missing, return null on the affected output and trigger a template fallback. We never ship empty-field generated text.
- Eval gate before scale: 200 deals across sub-categories, human review on accuracy (no fabricated facts), tone, cultural fit. Block on any merchant-data hallucination.

## 7. Fallback behavior

A two-tier fallback so the page is never broken:

1. **Per-field fallback:** if the model can't generate a field with confidence (missing inputs, eval-time flag), substitute the human-templated copy for that deal sub-category.
2. **Full fallback:** if more than two fields fall back, render the templated version end-to-end. This is the Arm B variant from E2 — and it's deliberately good enough to ship on its own. If AI never makes it past eval, we still have a meaningful product.

## 8. Where it integrates

| Surface | Use |
|---|---|
| Giftee landing (email / SMS / link tap) | Primary use. Server-side render on first load. Cached by `deal_id + giver_note_hash`. |
| Purchaser preview (at gift purchase) | Read-only render of the same artifact the giftee will see. Closes the Part 2 §2 confidence loop. |
| Reminder emails (Layer 2 nudge) | The scene_paragraph and cta_prompt are reusable inputs for the gentle nudge that fires 7 days post-delivery if the giftee hasn't planned a date. |
| Direct-purchase post-checkout (Part 1 E1) | Same primitive, applied to direct purchases. The giftee version is a strict superset (adds note + giver framing). |

## 9. Production notes

- **Latency:** target <1.2s p95 server-side render. Achievable with caching by `deal_id + giver_note_hash` — purchaser preview, giftee landing, and reminder content all read from one generated artifact.
- **Cost:** ~3K input tokens, ~400 output tokens per generation. At Groupon's gifting volume, cache hit rate >80% expected (most variation is the giver's note; deal-side context is stable per deal).
- **Model choice:** lightweight model (Haiku-tier) is enough for this. The task is constrained-slot generation, not reasoning. Reserve larger models for the eval pipeline that audits the outputs offline.
- **Eval pipeline (offline):**
  - Rule-based checks: no out-of-input facts (regex on phones, currencies, hours), no relational extrapolation (NER + relationship-term blocklist), word counts within bounds.
  - LLM-judge for tone alignment with the giver's note (matched / neutral / mismatched).
  - Human review on a rotating 50-deal sample per week, weighted toward new merchants and low-volume sub-categories.
- **Instrumentation:** log every generated artifact with input hash, output, eval verdict, and downstream behavior (commitment taken, redeemed). This is how we close the loop on which AI outputs actually move the metric — and how Part 1 E2's three-arm test gets clean data.

## 10. What I'd watch in the first 30 days post-launch

- Commitment-action rate on the giftee Welcome (the leading indicator from Part 1 §5, scoped to gifted purchases).
- Giftee activation rate (redemption within 30 days of gift delivery).
- AI fallback rate by sub-category — high fallback in a sub-category means merchant metadata is the bottleneck, not the AI.
- Purchaser repeat-gift rate (the downstream signal that purchaser confidence improved).
- Any spike in tone-mismatch flags from the offline judge — the early sign that the model is drifting.

## 11. What this prototype is NOT

- Not a visual finish. The styling is Groupon-adjacent but not pixel-final.
- Not a real model call. The three examples are pre-generated, not live. The point is to demonstrate the behavior is real — different deal types produce visibly different output across all four AI fields, not template-substitution masquerading as personalization.
- Not the entire gifting redesign. Stages 1 (gift purchase) and 2 (delivery) need their own work. This prototype focuses on Stage 3 because it's where the leverage is.
