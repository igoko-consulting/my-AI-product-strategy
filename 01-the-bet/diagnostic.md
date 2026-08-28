# Three-Axis Vulnerability Diagnostic

## Product
<!-- Name the product you're diagnosing. Real product at your company — not a hypothetical. -->
**Product:** Trip Disruption Copilot (AI feature for a travel/OTA platform)
**Your Role:** Product leader, domain grounded in real GPM experience in travel (Booking.com, Expedia) — applied as a live bet, not a hypothetical industry

---

## Scores

### Contextual Moat — 3/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:** Real feature-level stickiness, a traveler who's had a disruption resolved before they noticed trusts the platform more, and that's a genuine retention moment. But the moat is inherited from the host OTA, not built independently: it's a feature inside a larger product, not a standalone habit. Consistent with the data flywheel score (12/20, Correction 3/5, Preference 4/5), the compounding advantage is real but not yet structural. A rival OTA can ship the equivalent feature without needing to break any switching-cost barrier first.

**Named attacker (from partner challenge):** A full-stack OTA rival, e.g. Expedia, could ship an equivalent disruption copilot without overcoming any structural barrier, since the moat here is feature-level, not platform-level.

---

### Data Advantage — 4/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:** Strong. Full cross-airline, cross-hotel itinerary and rebooking-outcome history compounds with every disruption handled, no LLM vendor has this. The Preference loop (4/5) and Correction loop (3/5) on the flywheel both support this score directly. The one drag on confidence is the Network loop (2/5), a structural weakness, not a single distinct competitor, aggregate cross-supplier signal is thin compared to the personal booking history, so this axis is strong on individual compounding but weaker on collective compounding.

**Named attacker (from partner challenge):** Not a single distinct product. The risk is structural, the Network loop is where any platform with broader aggregate cross-supplier volume, e.g. Google via its aggregate flight-status reach, gradually erodes the collective-reliability piece of this advantage over time, even though it can't touch the personal-history piece.

---

### Platform Exposure — 3/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what?*

**Score rationale:** Real, quantified exposure, but partial, not total. Per the encroachment threat assessment, Google could ship a lightweight version inside Gmail/Flights within 6 to 12 months, since the itinerary-detection infrastructure (Gmail trip parsing) already exists today, that's a credible near-term threat, estimated at 40% of value at risk. But Google's version stops at the "alert" half of the value: actual rebooking execution still has to route through the OTA or airline to pay and confirm, which is the half we can defend by owning the transaction end to end.

**Named attacker (from partner challenge):** Google (Flights / Gmail trip parsing), bundled distribution and existing itinerary-detection infrastructure. Secondary threats named in the same assessment: a vertical disruption specialist (30% of value at risk, concentrated in compensation/claims) and card issuers with travel insurance (20%, mostly mindshare, not transaction value).

---

## Top Vulnerability
<!-- One line: what's the single biggest strategic risk? -->
Platform Exposure via Google: the highest-quantified single threat (40% of value at risk, 6-12 month timeline) of the three named encroachment vectors, though it only threatens the alert half of the value, not the execution half, which stays defensible as long as we own the end-to-end resolution flow.

## Confidence Level
<!-- H / M / L — how confident are you in this bet after the diagnostic? -->
M — no axis is structurally broken (lowest score is 3/5, not 1 or 2), the biggest named risk is partial rather than total, and a concrete defense already exists (own rebooking execution end to end so a platform alert becomes distribution, not a replacement).
