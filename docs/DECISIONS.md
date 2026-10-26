# WorkThatGodBod — design decisions and evidence

**Creative authority:** Babuni.dev.

This register distinguishes direct source observations from assumptions and from decisions Babuni.dev still needs to make.

## Current implementation evidence

| Topic | Code / history | Status and qualification |
| --- | --- | --- |
| Optional movement/hydration cues during play | Original README, `EXERCISES` | Stated project purpose and implemented text |
| No background alarm loop | `UseAction` wrapper; no OnUpdate timer | Implemented; a time **threshold** still exists |
| Several watched slots | `GOD.slots` and `slot/unslot/clear`; `db71577` | Changed from a one-slot v0.1 design |
| Minimal chat-only UI | `godChat`, `/godbod` parser | Implemented, but some messages are **nonlocal** |
| Chance and elapsed interval | `GOD_Trigger` | Failed chance still consumes interval |
| Per-character settings | `WorkThatGodBodDB.chars[charKey()]`; `9b67d16` | Account-wide TOC storage, logically separate entries |
| Fantasy-themed prose | January 24 rewrite `9b67d16` | Visible content change; authoring dialogue unavailable |
| Social message routing | `outputExercise` and January historical diffs | Source includes 14% nonlocal routes; reason/approval not recovered |

## Evolution, not invented deliberations

The first v0.1 source used one watched slot and local chat, with relatively plain prompts. A 2026-01-05 revision introduced random chat destination routing, including world/general channel codes. Subsequent commits added multi-slot support. On 2026-01-24, the code was refactored into a standalone 1.1 structure, introduced character-keyed saved settings and rewrote the prompt pool in fantasy language. The rewrite removed world/general sending, **but** retained party/say/yell and added guild sends.

The Git diffs prove these changes happened; they do **not** prove what discussions, safety evaluations, user approvals or rejection rationales led to them.

## Material discrepancy between README and source

The old README called the addon “zero UI, chat-only” and “no nagging,” without disclosing the 14% chance to route a produced prompt to other players. It also described one chosen slot, although the source supports many. The expanded README corrects these facts rather than silently modifying runtime behavior.

A separate source comment describes party messages as `95–96` only; actual `roll >= 95` selects `95–100` (**6%**). This is an implementation/comment discrepancy, not a tested statistical result.

## Open creator decisions

1. **Visibility and consent:** should reminders be strictly private by default? Should public routes require explicit opt-in?
2. **Time semantics:** should the cooldown restart on every eligible attempt, or only when a reminder is actually delivered?
3. **Intensity:** should some prompts be excluded/modified for accessibility or user preference?
4. **Character configuration:** should per-character settings remain nested in the account-wide DB, or use TOC-level character saved variables?
5. **Portfolio narrative:** how does the creator personally explain the move from straightforward reminders to Azeroth-themed writing?

This pass answered none of those questions on Babuni.dev's behalf. Only documentation changed.
