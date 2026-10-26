# WorkThatGodBod

**Creator and author:** Babuni.dev  
**Target:** World of Warcraft 1.12.1 / Interface `11200`  
**Current declared version:** **1.1**  
**Status:** Source inspected on 2026-10-26; **not tested in-game** during this documentation review.

**WorkThatGodBod** is a tiny roleplay-flavored prompt generator for real-life microbreaks during World of Warcraft. Pressing one of the action-bar slots you have chosen can occasionally produce a short, randomized prompt about **movement, posture, breathing, screen breaks, or drinking water**. The content blends everyday actions with fantasy imagery—stretching like a banner in the wind, refilling mana, or loosening adventurer joints.

It does **not** monitor your health, count completed exercises, or force a break. It integrates with action-button presses rather than interrupting you on a periodic background timer. The current source contains **99 unique prompts**.

## Important: some prompts are posted to other players

**The addon is not strictly private.** After a reminder qualifies, `outputExercise` randomly routes it to local chat **86%** of the time or attempts to send it to group/public-facing channels **14%** of the time:

| Output target | Share of qualifying reminders |
| --- | ---: |
| Local chat frame (only you) | 86% |
| Guild chat | 4% |
| Say | 2% |
| Yell | 2% |
| Party | 6% |

These are exact branches of the present source—not a verified distribution of **successfully delivered** messages. A send may fail when the player is not in the required group. The historical README presented the tool as quiet chat-only nudges but did not explain these transmissions. The addon **does not have a local-only toggle** in v1.1; `/godbod off` disables all prompts.

**This documentation corrects the description only.** It does not alter which messages are transmitted. The creator has not yet selected whether future behavior should be local-only or explicitly opt-in to sharing.

## Installation

Place `WorkThatGodBod.lua` and `WorkThatGodBod.toc` inside:

```text
Interface/
└── AddOns/
    └── WorkThatGodBod/
        ├── WorkThatGodBod.toc
        └── WorkThatGodBod.lua
```

Restart the game, enable the addon, and verify that it loads on your chosen 1.12-compatible client. This review did not perform that installation.

## Commands and setup

The current version supports **multiple watched action slots**. This differs from the original one-slot design and from the older README description.

| Command | Action |
| --- | --- |
| `/godbod watch` | Toggle showing action-bar slot numbers when buttons are pressed |
| `/godbod slot <number>` | **Add** an action slot to the watched set |
| `/godbod unslot <number>` | Remove one watched slot |
| `/godbod clear` | Remove **all** watched slots |
| `/godbod timer <seconds>` | Set minimum seconds between eligible prompt attempts (default **60**) |
| `/godbod chance <0-100>` | Set chance of producing a prompt on an eligible attempt (default **100%**) |
| `/godbod on`, `/godbod off` | Enable or disable reminders |
| `/godbod info` | Display watched-slot count, chance, timer, and enabled state |

For example, use `/godbod watch`, press an ability button, and note its slot. Use `/godbod slot 3` (adjust the number), then `/godbod watch` to stop printing slot numbers. Add further slots as wanted. To stop reminders altogether, use `/godbod off`.

There is **no** `/godbod cd` command in the current source. The current interval command is **`timer`**. The parser accepts command words case-insensitively.

## How the implementation behaves

The Lua wraps WoW's global `UseAction`. On each watched-slot press it checks enabled state, the interval since the previous eligible attempt, and a random percentage. The original action is then called with its arguments; WorkThatGodBod does not cast abilities for you.

The cooldown timestamp is updated **before** testing the random chance. A failed chance roll therefore still consumes the configured interval. There is no autonomous recurring timer or tracking of elapsed gaming-session duration; `GetTime()` is used as a gate when watched actions are pressed.

The TOC declares an **account-wide** `WorkThatGodBodDB` table, but the Lua stores each character's settings separately under `chars["name-realm"]`. Slot preferences, chance, interval, and enabled state are character-specific in that schema. There is no health-history or completed-activity log.

## A small wellbeing nudge, not medical guidance

Prompts are playful suggestions, not personalized exercises or instructions from a healthcare professional. Some propose balance, neck movement, squats or other movements that will not suit every player or environment. Skip anything uncomfortable or unsafe. The creator's original intention is a **gentle interruption of static play**, not a measure of physical performance.

## Development history and licensing

The repository began on **2025-12-14** as a simpler `v0.1` with one watched slot and local chat output. During **January 2026**, Git revisions expanded the prompt pool, added multiple slots, experimented with shared chat destinations, and reorganized preferences into per-character records. The significant **v1.1** rewrite on **2026-01-24** turned the prompts into Azeroth-themed writing and removed earlier `/world` and `/general` routes while retaining limited guild, say, yell, and party sends.

The project is released under its existing **MIT license**, which credits **Babuni.dev**. No runtime Lua, TOC or license file was changed for this documentation update.

## Development documentation

- [Concept](CONCEPT.md) · [Experience design](docs/DESIGN.md) · [Prompt/content inventory](docs/CONTENT.md)
- [Architecture](docs/ARCHITECTURE.md) · [Decisions and open questions](docs/DECISIONS.md) · [Narrative development journal](docs/DEVLOG.md)
- [Roadmap](ROADMAP.md) · [Changelog](CHANGELOG.md)
- [Human–AI collaboration](docs/AI_COLLABORATION.md) · [Developer rules](AGENTS.md)

**Attribution policy:** The project and creative direction are Babuni.dev's. Git diffs substantiate historical code/text changes, not unrecorded discussions or user approvals.
