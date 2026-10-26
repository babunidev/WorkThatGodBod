# WorkThatGodBod — prompt writing and content inventory

**Author:** Babuni.dev  
**Canonical text:** `EXERCISES` table in `WorkThatGodBod.lua`.

## Current corpus

The current v1.1 source contains **99 unique English-language prompt strings** in a single Lua table. Each selection is uniform across the same pool; there is no in-code category tag, preferred ordering, intensity scoring, or localization layer.

Representative wording:

> “Drink water as if refilling mana. Inhale deep. Exhale slow.”

> “Stand proud like an NPC with a backstory.”

> “Move joints gently. No force. Longevity matters.”

These examples demonstrate the desired relationship: a mundane real-world action is reframed as something a character might recognize in Azeroth. The text remains an *invitation*, not a measurement or requirement.

## Editorial motifs (not runtime categories)

| Editorial theme | Description |
| --- | --- |
| Hydration | Water as mana replenishment or a helpful buff |
| Posture | Shoulder alignment, neutral stance, jaw relaxation |
| Movement | Walking, marching, squats, stretches and joint motion |
| Eyes and screen breaks | Looking at the horizon, resting the eyes and blinking |
| Breath and calm | Gentle breathing, release of tension and quiet pauses |
| Humor and roleplay | Armor, dragons, taverns, NPCs, gryphons and warhorses |

No categories are selected in the code; one randomly chosen line can span multiple themes.

## Proven textual evolution

- Initial **v0.1** source on **2025-12-14** had a shorter, predominantly plain-language movement pool.
- A **2026-01-05** revision added many suggestions, then a **2026-01-06** change corrected a missing comma between list entries.
- The **2026-01-24** rewrite (`9b67d16`) replaced much of the plain phrasing with an expanded, consistent fantasy style. This is the strongest source evidence for the current content direction.

Git confirms changes to text; it does not establish which individual words Babuni.dev versus an AI assistant first drafted or why every metaphor was changed. Do not fabricate an authoring dialogue.

## Safety and content stewardship

The prompts are not medical recommendations. Particular movements will be inappropriate for some people, situations, or physical limitations, and the addon never observes whether one was done. Preserve the playful, optional character voice and include a clear ability to ignore prompts. A future filter or lower-intensity pool would require author approval.

Some prompts can be **shared in chat**. This affects both the player and recipients; content curation must consider context, consent and chat etiquette as well as style.

To edit the corpus, revise the canonical Lua table rather than maintaining a duplicated 99-line list here. Document why the creator chose the new tone, what actually changed and whether the client was tested.
