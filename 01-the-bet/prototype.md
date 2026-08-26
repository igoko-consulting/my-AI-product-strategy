# The Prototype Bet

## What I Built
<!-- One sentence: what does this prototype demonstrate? -->
A one-page travel booking prototype where the AI refines a vague search into ranked trips, then keeps watching the booked trip and proposes a rebooking before the airline cancels.

## Tool Used
<!-- v0 / Cursor / Lovable / other -->
Claude Code: Hand-built single-file HTML/CSS/JS, no framework.

## Prototype Link
<!-- Paste the shareable URL -->
https://claude.ai/code/artifact/61b922f7-67c9-4371-b934-31f31f0e4c96

## AI Value Archetype
<!-- Automator / Copilot / Oracle / Creator / Orchestrator -->
Copilot/Orchestrator: refines intent with the user, then acts across flights, hotel and transfers under user-set autonomy limits.

## The Bet in One Sentence
<!-- What you're building, for whom, why now -->
For travellers booking leisure trips, we bet that disruption handling, surfaced as risk at browse time and as a pre-held fix at disruption time, is worth switching booking platform for, now that airline and hotel inventory APIs make holding an alternative viable before the airline acts.

## Kill Criteria
<!-- When would you stop? What evidence would kill this bet? -->
Autonomy is refused: if most users pick notify-only, the orchestration never runs and the product is a normal booking site with extra steps.
Nobody changes their booking choice: if the disruption-risk pill doesn't shift selection away from cheaper high-risk itineraries, the browse-time value is imagined.
The fix isn't actually there: if held alternatives can't be secured at scale ahead of the airline, or cost more than the delay avoided, the core promise fails economically.
Approval comes too late: if users don't respond inside the hold window, ask-first collapses and the only workable mode is one they've already rejected.
