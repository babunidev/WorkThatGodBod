# WorkThatGodBod — changelog

**Creator:** Babuni.dev. Dates below refer to **Git commit activity**, not independently verified public releases.

## 2026-10-26 — documentation deepening

- Rewrote the user guide to reflect the **v1.1** source: multiple watched slots, 99 fantasy prompts, per-character data stored inside account-wide SavedVariables, and `timer` rather than an older `cd` command.
- Disclosed outbound PARTY, GUILD, SAY and YELL routing omitted from the previous README; computed the actual output bands from the code.
- Expanded concept, roadmap, architecture, experience/content design, decisions, narrative devlog, attribution and developer guidance.
- Distinguished original design goals, historical implementation changes and tests yet to be run.
- **Documentation-only change:** no Lua, TOC or MIT license edits, no in-game tests.

## Selected source-grounded milestones

| Date | Commit | Observable changes |
| --- | --- | --- |
| **2025-12-14** | `1c10ea1`, `8631405` | Created manifest and initial **v0.1** Lua with one watched action slot, approximately 50 straightforward exercise/hydration reminders, a 60-second cooldown and local chat output. |
| **2025-12-14** | `8bd285b` | Changed the local “GodBod” chat coloring/style. |
| **2026-01-05** | `0d7968e` | Marked v0.2; introduced randomized output that could include `/world` and `/general` channels, plus party, yell and say. |
| **2026-01-05** | `ccc36c7` | Added a large block of exercise prompts; the next day's `6b1ba89` revision corrected a missing list separator. |
| **2026-01-06** | `db71577` | Converted one watched slot to multiple slots with add/remove/clear commands. |
| **2026-01-24** | `9b67d16` | Reworked as **standalone v1.1**: rewrote prompt pool with fantasy framing, reorganized state into per-character records, changed command to `/godbod timer`, removed `/world` and `/general` routes while adding guild routing and retaining party/say/yell. |
| **2026-01-24** | `3984bb3`, `69af5a6` | Updated TOC to version 1.1 and later corrected README command wording from `cd` to `timer`. |
| **2026-09-18** | `b640b59` | Changed source/client descriptions to provider-neutral Vanilla 1.12 language. |
| **2026-10-26** | previous documentation commits | Standardized public Babuni.dev credit and added a minimal documentation scaffold prior to the current expansion. |

The wording and dates are sourced to actual Git changes. The original rationale behind each implementation decision, successful runtime tests and any private creator/AI discussion cannot be inferred from terse commit titles.
