# WorkThatGodBod — creative and technical development journal

**Creative author:** Babuni.dev  
**Reconstructed 2026-10-26** from the creator-facing README, the live Lua/TOC, and dated Git diffs. This is a **retrospective development record**, not an invented transcript of private human–AI discussions.

## The creative premise: make a tiny break feel like play

WorkThatGodBod begins with a problem familiar to people who spend long stretches in a game: a person can become so involved in the world on the screen that small acts like moving, drinking water or changing posture fade into the background. The original README presents a very specific tone for the solution: **“No timers, no UI, no nagging—just small nudges when you’re already in motion.”**

The concept belongs to Babuni.dev. Rather than putting a monitoring dashboard beside WoW, the project makes the existing action bar a low-friction trigger. The player chooses actions that happen naturally; every so often the addon selects a short, voluntary suggestion. A reminder does not compel or even track whether a movement was done. Its success is conceived as a small pause without turning recreation into another job.

This is an interpretation consistent with the original description and implementation. The repository does not preserve a prompt-by-prompt authoring record, so the exact first conversation and AI role in conceiving individual mechanics cannot be reconstructed.

## 14 December 2025: a simple, local first version

GitHub shows the addon manifest and initial Lua committed on **2025-12-14** (`1c10ea1`, `8631405`). The code header called itself **v0.1**. It used a single watched action slot, a 60-second interval, configurable probability, and short practical prompts. Its output went to the local chat frame, not to other players' channels. The text was mostly plain, with occasional playful phrasing.

A separate same-day change (`8bd285b`) altered the color presentation of the GodBod prefix. Such tiny revisions matter in aggregate: the tool was being shaped not only as a mechanism but as something comfortable to glance at while playing.

The first source did not collect health measurements or completed-exercise histories. That nontracking quality remains central to the implemented product.

## 5–6 January 2026: a bigger pool and a more complicated social footprint

On **2026-01-05**, commit `0d7968e` labeled the source **v0.2** and added a randomized output path. Some of the messages could now go to **world/general channels**, party, say or yell instead of remaining private. A separate same-day commit (`ccc36c7`) expanded the movement suggestions. The following day's `6b1ba89` corrected a missing comma in the list, a concrete example of a small technical fix amid content iteration.

On **2026-01-06**, `db71577` changed the interaction from watching exactly one action bar slot to a **set of slots** with add, remove and clear controls. This broadened how naturally the addon could appear in a player's moment-to-moment actions: it no longer required one special button to carry the whole experience.

There is an important tension here. A playful public message can make a reminder social, but for a tool described as gentle and low-pressure, unexpected broadcasting can be distracting for both sender and recipients. The source shows that the routing changed; the historical human rationale, risks considered and whether anyone explicitly endorsed those percentages are **not** available and should not be invented.

## 24 January 2026: the fantasy world enters the prose

The largest observed creative revision came on **2026-01-24**. Commit `9b67d16` changed the source header to **WorkThatGodBod (Standalone) v1.1** and replaced the largely straightforward exercise sentences with a much stronger fantasy register. A water break became a mana refill. A stretch might resemble a shield wall, a battle posture, a banner in the wind or loosening armor. These are not just synonyms; the writing bridges the physical player with Azeroth's sense of adventure.

The current source contains **99 unique prompts**, picked from one flat table. There is no formal distinction among hydration, stretching, balance, breath or eye-rest content. That randomness keeps the message selection playful and somewhat surprising, though it also means the tool cannot personalize which prompts are appropriate for someone.

The same January revision refactored the code into a `GOD` state object, introduced `/godbod timer` and stored settings separately in `WorkThatGodBodDB.chars[name-realm]`. The TOC still declares account-wide SavedVariables, but the application divides records by character. This is an important distinction between physical storage and player-facing configuration.

The social-output mechanism was also revised. World/general channel destinations disappeared; **guild** was added, while party, yell and say remained. A comment near the routing table describes party output as rolls 95–96, but the actual `if roll >= 95` branch covers 95–100. Thus, among qualifying reminders, the exact code selects **86% local, 4% guild, 2% say, 2% yell and 6% party**. A total of **14% is directed away from the local chat frame**. The code does not guarantee those messages reach recipients if the relevant group is unavailable.

Finally, source and manifest version labels were aligned in `3984bb3`, and README wording was updated to the `timer` command in `69af5a6`. That shows how implementation and public instructions gradually converged—though not entirely.

## 2026: documentation catches up with the actual behavior

On **2026-09-18**, a commit changed provider-specific client wording to Vanilla/World of Warcraft 1.12 terminology. On **2026-10-26**, earlier work standardized Babuni.dev author credit and introduced a small documentation scaffold.

This review found that the old README was still incomplete in two significant ways: it spoke about **one** watched slot despite the implemented multi-slot set, and it described a quiet local feeling without revealing the **nonlocal chat distribution**. The remedy here was documentation accuracy—not an unauthorized change of what the addon sends. The updated README now tells players where reminders can go and documents `unslot` and `clear`.

The assistant's role in this 2026 pass was to read the GitHub source and history, reconstruct the design evolution, count prompts, calculate output bands, draft a practical user guide and maintain an honest record of decisions. **No Lua, TOC or MIT license changed, and no live client was run.**

## What the creator still gets to decide

The future of WorkThatGodBod depends on the balance Babuni.dev wants between private encouragement and social play. Should messages ever go to others by default? Is the choice of all 99 prompts genuinely useful, or should players filter movements that do not suit them? Is a failed chance roll supposed to delay the next prompt? Which small modifications would retain the original invitation rather than turning it into an intrusive reminder service?

Those are **open creative and technical decisions**. The current record preserves the creator's project and the source's evolution without claiming the assistant knows the missing conversation.

**Verification boundary:** Git diffs and the Lua implementation were examined. Runtime loading, channel delivery, reminder frequency, saved-variable persistence, multi-addon coexistence and real-world usefulness remain unverified.
