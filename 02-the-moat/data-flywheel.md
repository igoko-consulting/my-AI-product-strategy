# Data Flywheel Map

> Score each loop 1-5. Your weakest loop is where competitors attack first.
> The four loops below are the M2 starting point - adapt if your product has 2 or 6 loops instead of 4.

## Flywheel Loops
| Loop | What It Measures | Score 1 | Score 5 | Score | How does the signal change future experience |
|------|------------------|---------|---------|-------|-----------------------------------------------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | 3/5 | Accept/reject/override on rebooking options sharpens the ranking model, fewer bad suggestions next disruption |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | 4/5 | Past bookings and rebooking choices narrow future options to what this traveler actually accepts |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | 3/5 | Urgency and cost-tolerance patterns learned on flights carry over to hotel and ground transport disruptions |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | 2/5 | More users on a route means better prediction of which suppliers to flag as risky, before the next traveler books |

### Correction Loop - 3/5
**What you capture today:** accept, reject, or manual override on each suggested rebooking.<br>
**How it compounds:** disruption events are rare per traveler, so volume builds slowly. Still, every override teaches the model what "acceptable" actually looks like, not just "technically valid."

### Preference Loop - 4/5
**What you capture today:** past bookings, price sensitivity, loyalty status, prior rebooking choices, events data, experience behavioural data (analytics).<br>
**How it compounds:** inherited from the host OTA's existing data, not built from scratch. Personalization gets sharp fast because the starting dataset is already rich.

### Domain Context Loop - 3/5
**What you capture today:** disruption type, resolution path, traveler reaction, tagged by category.<br>
**How it compounds:** real but not automatic. Flight and hotel disruption rules differ a lot supplier to supplier, so transfer needs deliberate design, not a free byproduct of usage.

### Network Loop - 2/5
**What you capture today:** aggregate delay and cancellation frequency by airline, route, and hotel property.<br>
**How it compounds:** weakest loop by nature here. It's a supplier-reliability signal, not a direct user-to-user network effect. Grows the pie slowly, not the moat.

**Total Flywheel Score: 12/20** <br>
**Weakest Loop:** Network <br>
**Fix for weakest loop:** stop treating this as a purely reactive signal. Surface supplier-risk warnings at the point of booking, before a disruption happens, so aggregate data creates value for every user upfront, not just for the ones who happen to get hit.


---

## Encroachment Threat Assessment

### 1. Platform Encroachment
**Attacker:** Google (Flights / Travel / Gmail trip parsing)

**Vector:** Gmail already parses booking confirmations and Google Flights already tracks flight status. Layering an LLM rebooking-suggestion feature on top is a roadmap decision, not a technical buildout.

**Time-to-threat:** 6 to 12 months, since the itinerary-detection infrastructure is already live today.

**% of value at risk:** 40%. Google can plausibly out-alert us, but rebooking execution still needs to route back through the OTA or airline to actually pay and confirm. The "suggest" half of the value is exposed, the "book it" half is defended by owning the transaction.

*(Assumption: Google prioritizes this as a feature, not a new standalone product, since travel isn't core to their business model.)*

### 2. Vertical Competitor
**Attacker:** A flight-disruption specialist (compensation-claim startups like AirHelp, pivoting into full rebooking)

**Vector:** Deep specialization in one niche: EU261-style compensation claims plus rebooking, aggregating disruption data across many OTAs' customers, not just ours.

**Time-to-threat:** 6 to 9 months. The compensation-claims piece already exists, pivoting into rebooking is incremental, not a cold start.

**% of value at risk:** 30%, concentrated specifically in the compensation and claims niche. Doesn't threaten the core booking relationship, but erodes the reason to trust us over a specialist for disruption handling specifically.

*(Assumption: this attacker can access disruption data across OTAs, not just ours, giving them a broader training signal than we have alone.)*

### 3. Adjacent Expansion
**Attacker:** Card issuers with travel insurance products (Amex, Chase Sapphire)

**Vector:** They already see the travel purchase and offer trip-delay insurance, regardless of which OTA or airline was used. Adding proactive rebooking assistance is "one more benefit," not a new product line.

**Time-to-threat:** 12 to 18 months. Slower mover, but existing insurance-claim infrastructure gives them a head start.

**% of value at risk:** 20%, mostly mindshare and trust, not transaction value. They'd likely still redirect the customer back to us or the airline to execute a change.

*(Assumption: card issuers don't currently have rebooking execution capability and would partner or redirect rather than build it themselves.)*


---

## 90-Day Encroachment Plan

*Your partner played the Big Tech attacker. What was their plan to kill you?*

**Attacker:**
**Attack vector (target the weakest loop):**
**Weeks 1-4 - what they ship:**
**Weeks 5-8 - how they poach users:**
**Weeks 9-12 - why users don't come back:**
**Your defense:**
