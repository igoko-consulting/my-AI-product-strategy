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


## Governance Policy

**Scope:**
**Autonomy boundaries:**
**Escalation triggers:**
**Audit cadence:**
**Regulatory exposure (EU AI Act / other):**

## Agent Topology
<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |

**Total tools found:**
**Tools after triage:**
**Estimated hidden spend:**


