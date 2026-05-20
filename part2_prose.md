# Phase 4 — Part 2 prose (drafted)

---

## §1. The Giftee Moment

**The highest-leverage moment is the giftee landing — the first time the recipient is in our product.** Earlier stages either don't move activation (gift purchase) or aren't product-leverage problems (delivery is a channel-and-deliverability problem). Later stages either inherit Part 1's work (redemption) or are gated on something that hasn't happened yet (giftee → customer conversion).

**Current state.** The giftee taps an email or SMS link and lands on a page that looks like a deal page with a "claim" CTA. Many flows gate sign-in or account creation before the gift is fully visible. The giver's note, if rendered at all, sits in a quote-box and doesn't frame the experience. There's no merchant context, no warmth, no next-step. A brand-new visitor — who didn't choose this deal — is treated as an existing customer with a transaction to manage.

**What breaks.**
1. **Cold start.** The giftee didn't pick the deal and may not know Groupon. The page assumes context they don't have.
2. **Friction before value.** Sign-in gates before the gift is seen — high cost, no visible value.
3. **Lost relational context.** The giver's note is the warmest signal in the journey and the current page demotes it.
4. **No commitment hook.** Same H2 problem as direct purchase — and worse, because the giftee has even less context to self-serve.
5. **No bridge to repeat.** The first impression is "figure this out yourself." That impression has to survive all the way to redemption for the giftee → customer conversion to happen.

**Redesigned experience — "The Welcome."**

A single-screen, AI-personalized giftee landing built on five moves:

1. **Name what they got in human terms.** "A 60-minute deep-tissue massage at Bliss Spa in Wicker Park, on Sarah" — not "Voucher #12345."
2. **Frame the giver.** The note is the headline, not a sidebar. If there's no note, AI generates a warm, deal-type-aware default ("Sarah picked this — we think she had your weekends in mind").
3. **Set the scene.** AI-generated short paragraph using merchant metadata: what the experience is, what's included, what to expect on arrival. Never invents facts the merchant didn't supply.
4. **Offer the commitment moment.** Same Layer-1 mechanic from Part 1 — deal-type-aware "Book now / Set reminder / Save for later" — sized for a user who may have never used Groupon.
5. **Defer the account.** Identity is implicit (tied to the gifted email/phone). We don't ask for credentials until booking or redemption. The first contact with Groupon is the gift, not a sign-up form.

**This is the same commitment primitive from Part 1, deployed in the highest-leverage cold-start moment in the product.** It doesn't require new infrastructure beyond the AI-generation layer that E2 already justifies. The giftee → customer conversion isn't a separate workstream — it's the natural downstream of a Welcome that earns trust on first contact.

---

## §2. Purchaser Confidence

**Improvement: a purchaser-visible "see what they'll see" preview at gift purchase, plus a three-state delivery and engagement timeline.**

Purchaser anxiety has a specific shape: *did it land, did it land well, will they use it.* Today the purchaser sees a "sent" confirmation, then nothing. Two pieces close the gap:

1. **At purchase:** an exact preview of the Welcome screen the giftee will receive, with the giver's note rendered live. The purchaser tunes the note in context, watches it land, and confirms the experience. This is the "what will they actually receive" answer the purchaser needs.
2. **After delivery:** a simple three-state timeline — *Delivered → Welcomed → Planned* — visible to the purchaser. No exposure of the giftee's specific date (privacy), just the signal that the gift was opened, met with a real Welcome, and acted on.

**Connection to the giftee redesign.** This works *only because* the giftee experience now has a Welcome worth previewing and a commitment step worth signaling. Without the Welcome, the "Planned" state has nothing to bind to and the preview shows nothing distinctive. The purchaser confidence improvement is downstream of the giftee redesign — the same product feature seen from two sides. Repeat gifting follows directly: the purchaser who sees their gift land well is the most likely person to gift again.

---

## §3. AI-Enabled Prototype

See `prototype.html` (and the production spec in `prototype_spec.md`).

The prototype demonstrates **"The Welcome"** for three gift types — a birthday spa, an anniversary dinner, a graduation experience — each rendered with AI-personalized framing, merchant context, and a deal-type-aware commitment CTA. The annotation panel calls out exactly what is AI-driven, what data feeds it, and what the production prompt schema looks like. The three examples are pre-generated to demonstrate the personalization is real (different tone, different next-step, different merchant context per deal type) rather than a single template with field substitution.
