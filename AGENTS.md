# WorkThatGodBod — development and documentation rules

**Creative author and decision-maker:** Babuni.dev.

## Preserve the concept and source-based history

The project is a friendly, optional World of Warcraft microbreak reminder toy. It is not a health assessment app, performance tracker or combat helper. The author owns the intention, writing direction and decisions. Cite evidence from the source, README and dated commits before asserting historical facts; clearly label reconstruction where no original chat is available.

Separate **user direction**, **AI suggestion**, **iteration**, **decision**, **actual modified files/commits** and **runtime verification**. Never invent acceptance, specific test outcomes or attributed prompt authorship.

## Required safety/UX honesty

- **Do not describe current output as “local-only”.** v1.1 selects nonlocal PARTY/GUILD/SAY/YELL for 14% of produced reminders in source. This may be unexpected; do not downplay it or invent a consent mechanism.
- The published source comment understates PARTY probability: `roll >= 95` spans 95–100, so **6%**, not “95-96”.
- The current code supports **multiple action slots** and stores separate character records under `WorkThatGodBodDB.chars[name-realm]`, even though the TOC itself declares account-wide SavedVariables.
- Prompts are suggestions, not personalized medical or exercise prescriptions. Offer players the option to skip unsafe or uncomfortable movement.
- `GOD.last` is a time gate for eligible attempts, **not** a background session-length tracker. A failed probability check still consumes an interval.

## Implementation discipline

1. Read `README.md`, `CONCEPT.md`, `docs/ARCHITECTURE.md`, `docs/DECISIONS.md`, `docs/DESIGN.md`, `docs/CONTENT.md` and `WorkThatGodBod.lua`.
2. Do not change chat routing, saved-data schema, prompt pool, probability or cooldown semantics without Babuni.dev's direction.
3. Maintain target WoW 1.12/Lua 5.0 conventions unless explicitly changed.
4. Preserve the delegation to original `UseAction`, and review conflicts with other action-hook addons.
5. Test actual client loading, commands, output channels, randomness, persistence, and UI before claiming success.
6. Update all relevant documentation alongside code changes; preserve MIT license and author credit.
7. Keep portfolio journal narratives publication-safe: no private chats, health data, credentials or other players' personal information.

The 2026-10-26 update was strictly documentary and did not alter gameplay.
