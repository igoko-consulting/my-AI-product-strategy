# Kill Switch Audit

## Vendor Dependency Assessment
| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | Single provider (Anthropic Claude), no fallback configured | H | This week: stand up a second provider account and route 5% of traffic to it as a live fallback test |
| **Abstraction** | Prompts and tool-calling hardcoded to Claude's API format, not behind a vendor-agnostic layer | H | This month: migrate calls behind a routing/abstraction layer (e.g. LiteLLM) so a provider swap is a config change, not a rewrite |
| **Routing** | No routing layer, all requests go direct to one provider, no automatic failover | H | This quarter: build failover logic that reroutes traffic on outage, latency spike, or pricing change, not just manual switch |
| **Eval** | Golden set built in M4: 12 rows against a 150-row v1 target, with a reliability contract defining pass thresholds | M | Delivered. Remaining work is volume, not existence: expand to 150 rows so a provider swap can be scored with confidence rather than indicatively |

*Three actions, staged: this week (eval set + fallback provider test), this month (abstraction layer), this quarter (automatic routing/failover). Eval comes first since nothing else is safe to ship without a way to check it didn't degrade quality. **Status: the eval set landed in M4**, which drops that row from H to M and makes the abstraction layer the binding constraint.*

## Portability Score
Locked. Three of four dimensions remain high risk; the eval dimension dropped to medium once the M4 golden set landed. Target after the three actions land: Partial this quarter, Ready once failover routing is live and tested under real traffic.

## If Anthropic (Claude) doubles pricing tomorrow:
Today: no real 48-hour response, we absorb the cost while emergency-wrapping the API calls behind an abstraction layer under pressure, worst time to do it.

Target state, once the three actions are done: flip a config flag to reroute majority traffic to the fallback provider, validate against the golden eval set, confirm quality holds, done inside 48 hours.

## If Anthropic (Claude) ships a competing product:
Not much defensible at the model layer, any provider can build a similar copilot. What's defensible is what a model vendor doesn't have: the proprietary itinerary and rebooking-outcome data (Correction 3/5, Preference 4/5 on the flywheel), and owning the end-to-end transaction, booking, payment, refund, so a competing product from the vendor still has to route through us or the airline to actually execute a change.

