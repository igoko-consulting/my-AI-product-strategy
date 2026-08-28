# Kill Switch Audit

## Vendor Dependency Assessment
| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | Single provider (Anthropic Claude), no fallback configured | H | This week: stand up a second provider account and route 5% of traffic to it as a live fallback test |
| **Abstraction** | Prompts and tool-calling hardcoded to Claude's API format, not behind a vendor-agnostic layer | H | This month: migrate calls behind a routing/abstraction layer (e.g. LiteLLM) so a provider swap is a config change, not a rewrite |
| **Routing** | No routing layer, all requests go direct to one provider, no automatic failover | H | This quarter: build failover logic that reroutes traffic on outage, latency spike, or pricing change, not just manual switch |
| **Eval** | No formal eval set, quality checked ad hoc during development | H | This week: build a golden set of disruption scenarios with known-good rebooking outputs, so any swap can be scored before rollout |

*Three actions, staged: this week (eval set + fallback provider test), this month (abstraction layer), this quarter (automatic routing/failover). Eval comes first since nothing else is safe to ship without a way to check it didn't degrade quality.*

## Portability Score
Locked. All four dimensions are high risk today. Target after the three actions land: Partial this quarter, Ready once failover routing is live and tested under real traffic.

## If Anthropic (Claude) doubles pricing tomorrow:
Today: no real 48-hour response, we absorb the cost while emergency-wrapping the API calls behind an abstraction layer under pressure, worst time to do it.

Target state, once the three actions are done: flip a config flag to reroute majority traffic to the fallback provider, validate against the golden eval set, confirm quality holds, done inside 48 hours.

## If Anthropic (Claude) ships a competing product:
Not much defensible at the model layer, any provider can build a similar copilot. What's defensible is what a model vendor doesn't have: the proprietary itinerary and rebooking-outcome data (Correction 3/5, Preference 4/5 on the flywheel), and owning the end-to-end transaction, booking, payment, refund, so a competing product from the vendor still has to route through us or the airline to actually execute a change.

