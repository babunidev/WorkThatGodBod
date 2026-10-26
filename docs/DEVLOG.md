# WorkThatGodBod — development record

**Author:** Babuni.dev

## Retrospective reconstruction — 2026-10-26

A minimalist WoW 1.12 reminder addon using action-button presses to occasionally prompt hydration, posture and short movement breaks. The committed implementation takes this form: WorkThatGodBod.lua and .toc implement a configured watched slot, chance and interval; /godbod controls behavior; saved settings are per character. No timer-driven nagging or health monitoring: prompts appear in chat only as optional action-triggered nudges.

The development sequence and historical iterations are not proven by this source snapshot. No decisions or tests have been invented. AI supplied the present documentation framework and retrospective analysis; Babuni.dev remains the project author.

Verify time-between-prompts, persistence and disabled behavior on a 1.12 client.
