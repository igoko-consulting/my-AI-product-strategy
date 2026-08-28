# Three-Axis Vulnerability Diagnostic

## Product
<!-- Name the product you're diagnosing. Real product at your company — not a hypothetical. -->
**Product:** Miro (collaborative whiteboard / visual workspace platform)
**Your Role:** Product leader, prior role at Miro — diagnostic applies real domain knowledge from direct experience, not a current live bet

---

## Scores

### Contextual Moat — 3/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:** Real, embedded workshop and facilitation habit teams build up template libraries and integrate boards into recurring rituals (planning, retros, workshops). But a board is inherently more disposable than a design file archive (Figma) or a long-lived doc/wiki (Notion): the switching cost is moderate, not extreme, because FigJam offers near feature-parity for most of the same jobs-to-be-done.

**Named attacker (from partner challenge):** FigJam (Figma) near feature-parity, and already open in the same workflow for design-adjacent teams.

---

### Data Advantage — 2/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:** Miro sees real-time collaboration and facilitation patterns at scale, but canvas data — sticky notes, freeform drawings, mixed media, inconsistent structure, is inherently messier and harder to compound into clean proprietary signal than structured text (docs, threaded messages). High volume of activity is not the same as high-quality, compounding signal. Revised down from an initial pass that conflated activity volume with data quality.

**Named attacker (from partner challenge):** Not a single distinct product,the risk is structural (data quality itself), and it's shared by FigJam and Microsoft Whiteboard/Loop, which have access to comparable canvas interaction data without a clearly stronger extraction advantage on either side.

---

### Platform Exposure — 2/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what?*

**Score rationale:** High exposure on two compounding fronts, not just feature parity. First, a legacy platform architecture and slower shipping speed mean Miro cannot out-ship a hyperscaler feature race even when it sees the threat coming in time. Second, hyperscaler compliance and enterprise trust (SOC2, data residency, existing procurement relationships) is a structural, pre-sold advantage, enterprise buyers default to the bundle they already trust, which a standalone vendor cannot out-build quickly. This is a harder problem than feature parity alone.

**Named attacker (from partner challenge):** Microsoft Whiteboard/Loop,bundled into Microsoft 365, with enterprise compliance and procurement relationships already sold. FigJam remains the faster, nimbler feature-parity threat on a separate front.

---

## Top Vulnerability
<!-- One line: what's the single biggest strategic risk? -->
Platform Exposure: Miro's legacy platform and slower shipping speed, combined with hyperscalers' pre-sold enterprise compliance trust, means Microsoft or Google can out-ship *and* out-sell an equivalent feature before Miro's workflow moat or data signal can compound enough to matter.

## Confidence Level
<!-- H / M / L — how confident are you in this bet after the diagnostic? -->
L — Two of three axes (Data, Platform) are structurally weak rather than merely feature-gap weak, and the weakest axis (Platform) is the hardest of the three to fix quickly.
