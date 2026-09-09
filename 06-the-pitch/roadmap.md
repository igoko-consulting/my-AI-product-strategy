# Three-Horizon Roadmap & Board Pitch

## Roadmap

*Horizons follow the AI-compressed cadence from the Roadmap Builder, not calendar quarters: Ship 0-4 weeks, Validate 1-3 months, Explore 3-6 months.*

### Horizon 1 — Ship (0-4 weeks)
*High confidence. Ship with existing capabilities.*

| Initiative | Strategy Component | Why it ships now | Confidence |
|---|---|---|---|
| Fifteen traveller interviews on switching intent and willingness to pay | Bet | No dependencies, no build, and it attacks the least-evidenced claim in the strategy | H |
| Peer red-team of the golden dataset by someone outside the project | Contract | Days of one person's time, and it closes an admitted gap the strategy already flags | H |
| Suppress the numeric confidence figure until calibration is measured | Contract | A display decision, not a build. Showing an uncalibrated percentage is worse than showing none | H |
| Align the all-reversible product copy with fare-rule reality once a ticket is reissued | Contract | Copy plus a commercial fact-check. The current claim is one the airline does not honour | H |
| Secure written carrier agreement to hold seats ahead of a cancellation announcement at one hub | Bet | A signed contract may take longer, but a yes-or-no answer is a four-week conversation | M |
| Staff and cost a 24/7 travel-ops reviewer rota | Guardrails | A costing exercise, not a hiring round. The current $0.10 per trip-month is almost certainly wrong | H |
| Expand golden dataset from 10 rows to the 150-row v1 target | Contract | Authoring work with a known format and no external dependency | M |
| Instrument autonomy-setting adoption after a traveller's first successful save | Margin | Small analytics change, and it is the metric the whole revenue model rests on | M |

### Horizon 2 — Validate (1-3 months)
*Strategic bets. Each carries a named hypothesis and kill criteria.*

| Initiative | Strategy Component | Hypothesis | Kill Criteria | Confidence |
|---|---|---|---|---|
| Browse-time disruption risk pill A/B on existing OTA traffic | Bet | Showing disruption risk at browse time shifts selection away from cheap high-risk itineraries | If selection mix does not move by 3pp by week 6, browse-time value is imagined and the pill comes out | H |
| Counterfactual outcome logging covering original flight status and hold conversion and actual arrival | Moat | Logging what actually happened makes disruption probability calibrated and proprietary | If calibration error does not fall by week 8, the predictor is not learnable at our volume | M |
| Resolve PSD2 strong customer authentication for auto-rebook via a merchant-initiated mandate | Guardrails | An MIT mandate agreed at opt-in is a compliant route to charging an absent traveller | If no compliant path is confirmed by week 8, auto-rebook leaves the roadmap and pricing is rebuilt around ask-first | M |
| Vendor abstraction layer so a provider swap is a config change rather than a rewrite | Moat | Portability is achievable without material quality loss, evidenced against the golden set | If a swap is not a config change by week 8, accept lock-in and price the risk explicitly | H |
| Show reasoning and trade-offs on rebooking options so travellers stop seeking a second opinion | Contract | The second-opinion behaviour is a trust gap we created and can close with visible reasoning | If second-opinion mentions in support contacts do not fall by week 10, the trust gap is elsewhere | M |
| Tiered base fee by trip value band holding the per-resolution fee flat | Margin | Willingness to pay scales with trip value, so a flat fee leaves money on high-value trips | If attach rate at the top band is worse than flat pricing by week 8, revert to flat | M |
| Extend disruption risk scoring to itineraries we did not sell | Bet | The workaround travellers already run manually is an acquisition wedge, not just a feature | If it does not produce qualified booking sessions by week 10, it is a feature and we stop funding it as growth | L |

### Horizon 3 — Explore (3-6 months)
*Low confidence. Small-investment experiments.*

| Initiative | Strategy Component | What must be true first | Confidence |
|---|---|---|---|
| Carrier and hub reliability index built from our own resolved cases | Moat | Counterfactual logging closed, and enough resolved cases per route to be statistically useful | M |
| Train our own option-ranking model on accept and reject data | Moat | Meaningful accept and reject volume, which requires the product to be live at scale | L |
| Automatic failover routing across model providers on outage or latency or price change | Moat | Abstraction layer shipped and validated against the golden set | M |
| EU261 claims partnership with a specialist provider rather than building it | Guardrails | Partner discovery done, and the regulatory boundary confirmed with counsel | L |
| Disruption and spend export for travel admins | Bet | That a business-travel buyer exists for us at all, which the strategy does not currently claim | L |

### Unmapped (cut or rethink)

| Initiative | Why it's unmapped | Recommendation |
|---|---|---|
| Disruption and spend export for travel admins | Held in H3 above under the original mapping, but the Bet names leisure travellers on an OTA. This serves a business-travel buyer no component supports | Rethink as a separate bet with its own validation, or cut |

### Mapping Disagreements

| Initiative | Mapped to | Would map to | Why |
|---|---|---|---|
| Disruption and spend export for travel admins | Bet | Unmapped | The Bet is explicit about leisure travellers, so this is scope drift into a different buyer rather than an expression of the stated bet |
| Staff and cost a 24/7 travel-ops reviewer rota | Guardrails | Margin | The action is correcting a COGS line that understates a follow-the-sun rota at $0.10 per trip-month; the policy question was already settled in Guardrails |

### Reading the spread

**Over-indexed horizon.** H1 is Contract-heavy — four of eight items polish the trust component while the bet itself stays unvalidated, and H2 carries almost all the risk-reducing work. H3 has nothing testing demand or pricing at scale.

**The H3 bet to protect if budget is cut.** The carrier and hub reliability index. It is the only asset that compounds across users and cannot be handed to a competitor by the next frontier release.

**The one initiative to kill today.** The travel-admin export. It serves a buyer the strategy does not claim, and funding it before the leisure bet is validated is the clearest scope drift in the backlog.

**One caveat across the whole roadmap.** Several H1 and H2 items — autonomy instrumentation, second-opinion measurement, tiered pricing tests — assume a live product with traffic. If it is not live, they are not four-week items and the horizon spread is optimistic by a quarter.

## AI Evaluation

*Generated with the AI Bet Evaluator against all five strategy components, all eight dimensions selected. Caveat: run by the same assistant that helped build the strategy, so it is a self-evaluation and worth less than an independent one.*

| Dimension | Score | Strengths | Gaps | Recommendation |
|---|---|---|---|---|
| Bet Validation | 2/5 | Four explicit falsifiable kill criteria, each tied to observable behaviour. Clear archetype and why-now | No user evidence of any kind. The central assumption that disruption handling is worth switching platform for is asserted, never tested. Validation speed unstated | Run the cheapest kill-criterion test first: a browse-time risk pill A/B measuring selection shift, which validates in weeks without building the copilot |
| Capability Assessment | 2/5 | Cascading architecture specified and costed. Agent topology names what each component can and cannot do | The crux capability — holding inventory ahead of the airline's announcement — is assumed and evidenced nowhere. Counterfactual logging does not exist, so the predictor cannot be trained. 24/7 reviewers carried at $0.10 per trip-month understates a follow-the-sun rota | Treat the hold premise as a commercial dependency, not a technical one, and get written confirmation from one carrier before further build |
| Impact Analysis | 3/5 | The 0.9% conversion-lift breakeven converts the whole investment case into one testable behavioural claim | No market sizing: trips, book of business, revenue at scale all absent. Opportunity cost never discussed. Compounding is half-broken by the strategy's own freeze test | Size the addressable book so the 0.9% lift can be expressed as money rather than a percentage |
| Defensibility Check | 2/5 | Unusually honest: scores its own moat at 12/20, concedes feature-level not platform-level, names Google with a timeline and value at risk | Half the flywheel does not run. Switching costs never named. Workflow depth is shallow — a feature inside someone else's funnel, with a moat inherited from the host OTA | Build Network Intelligence, the route and carrier reliability index. The only asset that compounds across users and cannot be bought from a model vendor |
| Pricing Alignment | 3/5 | The most rigorous section. Outcome-weighted hybrid matched to how value arrives, stress-tested at 3x, thresholds computed. Power-user question answered by separating monitoring intensity from disruption frequency | Zero willingness-to-pay evidence. $6.49 and $35.00 are both invented. The flat fee is regressive against trip value, noted and unresolved | Price-test the base fee against travel insurance at point of booking, where the comparison is already in the traveller's head |
| Trust & Reliability | 4/5 | Strongest component. Genuine adversarial rows including prompt injection through ingested content. Contract with measurement methods, thresholds and consequences. Confidence tiered on the action rather than the prediction | 10 rows against a 150 target, so the contract runs far ahead of what exists. Nothing measured yet, so every target is a promise. The confidence percentage is uncalibrated because Outcome Calibration is broken | Do not ship the numeric confidence figure until calibration is measured. An uncalibrated percentage is worse than none |
| Governance & Scale | 4/5 | Autonomy boundaries are decision-level, not tier-level. GDPR Article 22 correctly identified as the binding constraint rather than the EU AI Act. No agent both decides and executes an irreversible action. Shadow AI audit done as roadmap input, not security theatre | PSD2 SCA unexamined, and it threatens auto-rebook, the tier the revenue model depends on. The storm month is modelled for cost but not for reviewer load, so the human path fails when most needed | Resolve SCA before committing to auto-rebook. It is a binary blocker on the revenue-critical tier |
| Gap Identification | 4/5 | Names its own weaknesses rather than hiding them: the $20 attribution, the missing peer red-team, the reversibility contradiction, the uncalibrated confidence figure | The weakest component is the Bet, and everything downstream is rigorous work built on an unvalidated premise | Stop deepening the downstream components. Every additional hour on contract and guardrails increases the sunk cost behind an untested bet |

**Overall score: 3/5.** Rigour is high and evidence is absent. This is a well-engineered answer to a question nobody has yet confirmed is being asked, which is a better failure mode than the reverse, but it is still the position it is in.

**Biggest risk.** The inventory-hold premise. The product rests on holding a seat or room before the airline announces the cancellation. If carriers will not permit that at scale, or price it punitively, the leader feature evaporates and every other component becomes scaffolding around a hole. This outranks Google encroachment because it is binary, near-term, and answerable in weeks.

**Top three actions.**

1. **Test the hold premise commercially.** One carrier, one hub, written confirmation. Weeks, not months, and the answer is binary.
2. **Get switching and willingness-to-pay evidence from real travellers.** Fifteen interviews plus the browse-time risk-pill A/B. Two of the four kill criteria are testable this way without building the copilot.
3. **Close Outcome Calibration.** Cheap, unblocks the confidence figure the trust model depends on, and it is the only loop that turns usage into a predictor a frontier release cannot hand a competitor for free.

*All three actions appear in the roadmap above: actions 1 and 2 in Horizon 1, action 3 in Horizon 2.*

## Board Pitch

**Thesis (1 sentence):**

**The case:**
1. Why now:
2. What's defensible:
3. The economics:

**The risks:**
1. Trust / failure modes:
2. Scale / governance:
3. Competitive:

**The ask:**

## M1 Baseline vs. Now
*Your 3-sentence AI strategy from Module 1 vs. what you'd say now:*

**M1 baseline:**

**Now:**
