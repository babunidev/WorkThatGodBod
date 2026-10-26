# WorkThatGodBod — concept

**Creative author:** Babuni.dev  
**Format:** lightweight World of Warcraft addon for voluntary real-world microbreak prompts.

## A moment of movement inside the game

The idea is modest and appealing: instead of asking a player to run a fitness app alongside an evening of World of Warcraft, attach occasional suggestions to an action they already perform. A button press sometimes produces a small invitation to move, shift posture, rest eyes, take a few breaths, or drink water.

The original project README sets the tone: **“No timers, no UI, no nagging—just small nudges when you’re already in motion.”** Its meaning is that the addon does not continuously interrupt with scheduled alarms. The current implementation **does** use a configurable elapsed-time threshold to space out eligible prompts. Those are compatible distinctions as long as documentation says “no background alarm,” rather than literally “no timing.”

## Fantasy gives ordinary care a playful voice

The current text pool narrates mundane gestures in familiar Azeroth language. Water becomes a mana refill. Rolling shoulders becomes loosening worn armor. Looking away from a screen resembles watching the horizon for gryphons. That framing connects the player to their game world while inviting a short, voluntary real-world action.

The repository's January 24, 2026 source rewrite demonstrates the transition from mostly plain exercise instructions to **fantasy-themed micro-prompts**. That is evidence of a change to the creative expression. The original discussion and who proposed every individual metaphor are not recorded, so they are not invented here.

## Design principles supported by the source

- **Voluntary:** `/godbod off` disables the nudge; no compliance reporting exists.
- **Action-associated:** checks occur when the user presses configured action slots, not on a repeating background alarm.
- **Occasional:** a configurable interval and chance control frequency; chance failure still consumes an interval.
- **Minimal UI:** feedback uses text chat; there is no overlay, exercise log or progress bar.
- **Game-world flavor:** 99 unique written prompts mix hydration, posture, breath, balance and movement with fantasy references.
- **Character-specific preferences:** the account-wide saved table is organized by character name and realm.

## Important tension with the original quiet intent

Although the README describes private-feeling “small nudges,” source v1.1 intentionally routes a minority of emitted messages to PARTY, GUILD, SAY or YELL. **14% of qualifying reminders are sent to one of those nonlocal destinations, not merely shown privately.** The reasons for this design choice are not established by the available conversations. Public delivery, possible spam and player consent are unresolved creative decisions, not silently endorsed features.

## Boundaries

This is **not** medical advice, health tracking, an inactivity detector, an automatic workout planner, or a competitive fitness product. It does not verify that the prompted action was completed. The document is a source-grounded concept reconstruction; only explicit future creator decisions should change its scope.
