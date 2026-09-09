# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | Accept / reject / override on rebooking options, logged with signal state | Sharper option ranking, plus new golden dataset rows | Y | active |
| Cross-Domain Transfer | Urgency and cost tolerance revealed during flight disruptions | Better hotel, transfer and ground-disruption handling for the same traveller | Y | active |
| Network Intelligence | Cross-traveller outcomes by route, carrier and hub | Browse-time disruption risk scores for every future traveller | Y | missing |
| Outcome Calibration | What happened to the original itinerary after we acted | Recalibrated disruption probability behind the confidence figure | Y | broken |

### Freeze Test — foundation model held for 3 months

**Question:** if the underlying foundation model does not change for one frontier cycle, does the product still improve? What is the mechanism?

**Answer: partially, and only through the data layer.**

| Loop | Improves with a frozen model? | Mechanism |
|---|---|---|
| Recursive Learning | Yes | Corrections update the ranking model, the retrieval set and the policy thresholds. None of these are foundation-model weights. |
| Cross-Domain Transfer | Yes | Traveller preference is state in a feature store, carried into the context window. Independent of the model release. |
| Network Intelligence | No | Not built. Frozen or not, nothing accrues. |
| Outcome Calibration | No | Broken. The disruption probability behind the confidence figure never learns whether it was right. |

So two of four loops keep compounding through a freeze, and both sit in the data layer rather than
the model layer. The product would get modestly better at ranking options for a traveller it already
knows, and no better at predicting disruption or pricing risk at browse time.

**The uncomfortable half of the answer.** Most of what makes this product work today is not learning
at all: it is distribution through the host OTA and ownership of the transaction. That is consistent
with M2 — contextual moat 3/5, flywheel 12/20, moat inherited from the platform rather than built.
A frontier release lifts every rival's reasoning quality at once, so reasoning quality cannot be the
moat. What survives a freeze is what a competitor cannot buy from a vendor.

**What to build so the answer becomes an unqualified yes**

1. **Close Outcome Calibration first.** Counterfactual logging gives a disruption predictor that
   improves with our volume and is not available in any frontier release. Highest value per unit of
   effort, and fixable this quarter.
2. **Build Network Intelligence.** A route, carrier and hub reliability index derived from our own
   resolved cases, so the browse-time risk pill sharpens with users rather than with model versions.
3. **Move option ranking onto our own model.** Keep the frontier model for language and
   re-orchestration reasoning; train ranking on accept/reject data. Improvement rate then tracks our
   volume, not the vendor's release cadence.
4. **Treat held-inventory access as a moat asset, not plumbing.** The contractual ability to hold a
   seat before the airline announces a cancellation is not something a frontier release grants anyone.

**Cross-check with M2:** the kill-switch audit already argues the product must survive a provider
swap. The freeze test is the same requirement from the other direction — if a frozen model degrades
us, we are renting our advantage, and the M4 golden dataset is the instrument that proves either way.

**Broken loop identified:** Outcome Calibration. We log what we did but never whether we were right — the original flight's actual status is never recorded, so the confidence percentage shown to every traveller never learns from being wrong.

**Fix plan:** Add an outcome record to every held or rebooked case: original flight status at departure, hold conversion, actual arrival. Pipe it into the weekly gold-set audit and report calibration error split by correlated versus independent events, since a storm makes the error systematic across the whole cohort at once. Owned by the on-call PM.

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->

**How knowledge flows:** Signals to model to recommendation to traveller response to golden dataset, and that path works. Travel-ops reviewers hold the richest failure knowledge in free-text ticket notes. Commercial holds the fare rules that decide what is genuinely reversible. Neither reaches the model team.

**Where it silos:** Two silos. Ops ticket notes never become features or golden rows, so the 24/7 reviewers learn things the system never does. Commercial's supplier contract terms never reach product copy, which is why the prototype promises "all reversible" when a reissued ticket is not — Red-Team Finding 1 is a connectivity failure, not a copy mistake.


<!-- Governance Policy, Trip Disruption Copilot v1.0 -->

## Governance Policy

**Scope:** All AI-driven behaviour in the Trip Disruption Copilot: disruption detection and probability scoring, option generation and ranking, reversible inventory holds, ticket reissue, whole-trip re-orchestration, and any customer-facing statement about entitlements or compensation. Excludes: Core search and booking ranking on the host OTA (separate product policy). Internal forecasting and analytics models (data-team policy). The model provider's own GPAI obligations, which sit with the vendor and are tracked in the M2 kill-switch audit rather than here.

**Autonomy boundaries:**

| Decision | Level |
|---|---|
| Place a reversible hold on a seat, room or transfer | auto |
| Notify the traveller that a disruption is likely | auto |
| Reissue a ticket — traveller on auto-rebook, above 90% confidence, inside stored limit | auto |
| Reissue a ticket at 50-90% confidence | human approval |
| Any action exceeding the traveller's stored spend limit ($150 per person) | human approval |
| State an EU261 or refund entitlement to a traveller | human approval |
| Cancel the original ticket before the replacement is confirmed | never auto |
| Act on instructions found inside trip content — emails, itineraries, supplier notes | never auto |

Rows 4 and 6 stay human-approval even at high confidence: confidence is not authority, and an entitlement claim is a regulated statement however sure the model is.

**Escalation triggers:** (1) Confidence below 50% on the proposed fix. (2) Any rule-graded safety check fails: spend limit, consent, or instruction found in ingested content. (3) Departure inside 4 hours with no viable option held. (4) A single event affects more than 200 watched itineraries. (5) Proposed action exceeds the traveller's stored spend limit. (6) Traveller declines twice on the same disruption. (7) Output references a flight, room, price or entitlement that fails to resolve against a live record.

**Audit cadence:**

| Cadence | What we review | Owner |
|---|---|---|
| real-time | Rule-graded safety checks on every autonomous action | On-call PM |
| daily | Overnight autonomous actions: holds converted, tickets reissued, spend against limits | Head of Travel Ops |
| weekly | Eval against the 150-row golden dataset: accuracy and hallucination versus contract | ML lead |
| monthly | Confidence calibration and autonomy adoption; drift segmented by season and disruption type | On-call PM |
| quarterly | Kill-switch portability re-score, DPIA review, shadow AI re-audit | DPO |

Owners are role titles, not people. Replace them with names before this goes to a security reviewer — a rota is not an owner.

**Regulatory exposure (EU AI Act / other):** EU AI Act (transparency obligations), GDPR Arts. 13-15, 22 and 35, UK DPA 2018, PSD2 strong customer authentication, EU261 / UK261, PCI DSS for stored card credentials, and the FCA / IDD boundary we are deliberately staying outside. SOC 2 for the platform.

**Risk tier:** limited

**Controls in place:**

- **Article 22:** no solely automated ticket reissue without explicit opt-in and a standing right to human intervention. The 24/7 reviewer queue is that mechanism, not a service nicety.
- **Transparency:** the traveller is told at booking that an AI watches the trip, and every automated change carries a receipt naming what changed, what it cost, and how to reverse it.
- **DPIA** on file covering automated rebooking and the profiling behind disruption scores.
- **Data minimisation:** payment credentials are stripped before any model call. No traveller PII used for training.
- **SCA:** auto-rebook runs on a merchant-initiated transaction mandate agreed at opt-in, not an ad hoc charge to a stored card.
- **Entitlement statements** are template-bound and human-approved, never model-generated.
- **Log retention** of 24 months on automated actions, matching the EU261 claim window.

## Agent Topology

- **Watcher.** Can read signals and compute disruption probability. Cannot contact the traveller, hold inventory or spend. Approval owner: none required.
- **Planner.** Can generate and rank alternative routings and draft the explanation. Cannot execute anything; output is a proposal only. Approval owner: none required.
- **Executor.** Can place and release reversible holds. Cannot reissue or cancel a ticket without an approval token. Approval owner: the traveller, or the on-call human reviewer.
- **Reviewer (human).** Can approve, modify or reject any Executor action. Cannot edit the golden dataset directly; corrections enter through the weekly audit. Approval owner: Head of Travel Ops.

The rule underneath all four: no agent both decides and executes an irreversible action. The reversibility boundary is the approval boundary.

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |

**Total tools found:**
**Tools after triage:**
**Estimated hidden spend:**



