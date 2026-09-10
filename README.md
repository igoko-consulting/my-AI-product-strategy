# My AI Product Strategy

> A living strategy built across 6 sessions. Each module adds one component. By Module 6, this repo IS your strategy — version-controlled, board-ready, portable.

**Product: Trip Disruption Copilot.** An AI copilot inside a travel booking platform that watches a booked trip, detects flight and hotel disruption before the airline announces it, holds the alternative, and rebooks on one tap.

All financial and operational figures are modelled, not disclosed.

---

## Strategy at a Glance

| Component | Module | Status | Key Artifact |
|-----------|--------|--------|-------------|
| **The Bet** | M1 | [x] | `01-the-bet/` |
| **The Moat** | M2 | [x] | `02-the-moat/` |
| **The Margin** | M3 | [x] | `03-the-margin/` |
| **The Contract** | M4 | [x] | `04-the-contract/` |
| **The Guardrails** | M5 | [x] | `05-the-guardrails/` |
| **The Pitch** | M6 | [x] | `06-the-pitch/` |

**Self-evaluation: 3/5.** Rigour is high, evidence is absent. Trust, governance and gap identification score 4/5; bet validation and capability score 2/5 because no traveller and no carrier has been asked yet. Full scoring in [`06-the-pitch/roadmap.md`](06-the-pitch/roadmap.md).

---

## The Bet (M1)

**What we're building, for whom, why now.**

- **Product:** Trip Disruption Copilot for leisure travellers on an OTA. Detects disruption before the airline announces it, holds the alternative, rebooks on one tap.
- **AI Value Archetype:** Copilot / Orchestrator
- **Vulnerability Scores:** Moat 3/5 · Data 4/5 · Platform 3/5
- **Top Risk:** Platform encroachment via Google — Gmail trip parsing already exists, so a lightweight version is 6–12 months away, roughly 40% of value at risk. The M6 evaluation later named a larger near-term risk: carriers may not permit holding inventory ahead of their own cancellation announcement.
- **Confidence:** M
- **Prototype:** Built and demoable. A single-page interactive prototype covering search, AI-led refinement, ranked options with disruption-risk scoring, the autonomy/guardian setup, and a live disruption-to-rebooking flow. Not publicly linked while the idea is live — available on request, and shown on screen in interviews.
- **Research:** Five [proxy interviews](01-the-bet/proxy-interviews.md) run against the prototype — family members role-playing target personas. Evidences comprehension, not demand. No actual disrupted traveller and no carrier has been asked anything.
- **Kill Criteria:** autonomy is refused and most users stay on notify-only · the disruption-risk pill does not shift booking selection · held alternatives cannot be secured at scale or cost more than the delay avoided · users do not respond inside the hold window

→ Details: [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

**Why this won't get copied in 6 months.**

- **Data Flywheel Score:** 12/20 — Correction 3 · Preference 4 · Domain Context 3 · Network 2
- **Weakest Loop:** Network, 2/5. Aggregate cross-supplier signal is thin compared with personal booking history.
- **Competitive Position:** Feature-level, not platform-level. The moat is inherited from the host OTA rather than built independently. A rival OTA can ship the equivalent without breaking a switching-cost barrier.
- **Encroachment Defense:** Own the transaction end to end. Google can take the alerting half; moving a booking still requires holding inventory, taking payment and reissuing the ticket, which routes through us.
- **Vendor Portability:** Locked — single provider, no abstraction layer, no failover. Three staged actions to reach Ready.

→ Details: [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

**Will this make money or bleed it?**

- **Gross Margin (current):** 94.0% — commission-only, ~$200 per completed trip on a $2,300 booking
- **Gross Margin (AI-adjusted):** 93.4% blended, or 91.0% on the copilot's own revenue line. Holds 58.5% through a correlated storm month.
- **Pricing Model:** Hybrid base plus usage, weighted to outcome. Penetrate posture. $6.49 per active trip-month plus $35.00 per disruption resolved.
- **Cascading Strategy:** 94% of requests never reach the frontier model. Blended $0.0021 per request, with 7.7× headroom before margin hits 40%.
- **Break-even at:** a **0.9% lift** in conversion or repeat booking. $1.80 COGS per active trip against ~$200 of commission.

→ Details: [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

**Why users will trust a probabilistic system.**

- **Reliability Target:** 93% accuracy with a separate 100% gate on rule-graded safety rows · hallucination under 0.5% · under 2s p95 and 90s signal-to-hold · drift under 0.5%/wk
- **Golden Dataset:** 12 rows at v1 against a 150-row target, 3 adversarial, 67% edge cases
- **Confidence UX:** Tiered on confidence in the *action*, not the prediction. Below 50%, no plan is presented at all.
- **HITL Architecture:** Confidence below 50%, a safety flag, departure inside 4 hours with no option, a correlated event over 200 itineraries, or any action above the stored spend limit routes to a 24/7 travel-ops reviewer whose corrections become golden rows.
- **Failure Mode Coverage:** 5 coverage gaps logged and 2 red-team findings, including a product claim the system cannot keep — "all reversible" stops being true once a ticket is reissued.

→ Details: [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

**What breaks when this scales — and what compounds.**

- **Compounding System:** 4 loops. Recursive Learning and Cross-Domain Transfer active; Outcome Calibration broken; Network Intelligence missing. Under a 3-month model freeze the product barely improves, which is the honest read on where the advantage currently comes from.
- **Governance Posture:** 8 autonomy decisions split across auto, human-approval and never-auto. Entitlement statements and mid-confidence ticket reissues stay human-approved regardless of model confidence.
- **Shadow AI Status:** 6 user-side workarounds found, 6 triaged — 3 build, 1 partner, 2 ignore. $89/month adjacent spend. Dominant signal: capability gap.
- **Agent Boundaries:** Watcher, Planner, Executor, human Reviewer. No agent both decides and executes an irreversible action.
- **Regulatory Exposure:** GDPR Article 22 is the binding constraint on auto-rebook · EU AI Act limited-risk, transparency obligations · PSD2 strong customer authentication unresolved and capable of removing the automatic tier.

→ Details: [`05-the-guardrails/`](05-the-guardrails/)

---

## The Pitch (M6)

**How you get this funded, shipped, and adopted.**

- **Horizon 1 (Now, 0–4 weeks):** 8 items. Traveller interviews, the carrier hold agreement, peer red-team, suppress the uncalibrated confidence figure, fix the reversibility copy, cost the 24/7 rota, golden dataset to 150 rows, instrument autonomy adoption.
- **Horizon 2 (Next, 1–3 months):** 7 items, each with kill criteria. Browse-time risk pill A/B, counterfactual outcome logging, PSD2 SCA resolution, vendor abstraction layer, visible reasoning on rebooking options, tiered base fee, risk scoring for itineraries we did not sell.
- **Horizon 3 (Bet, 3–6 months):** 5 items. Reliability index, own ranking model, provider failover, EU261 claims partnership, and a travel-admin export flagged as scope drift and a candidate to cut.
- **Board Narrative:** For leisure travellers, we turn the worst moment of a trip into the reason they book with us again, by fixing disruption before they know it has happened.
- **Key Metric:** Autonomy-setting adoption after a traveller's first successful save. Notify-only users generate no billable outcome, so this single number decides whether the revenue model works.
- **The Ask:** $250,000 as a budget shift, 4.5 reallocated people, 14 weeks to a Go/No-Go, hard stop at week 4 on the carrier answer.

→ Details: [`06-the-pitch/`](06-the-pitch/)
