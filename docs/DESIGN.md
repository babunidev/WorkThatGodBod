# WorkThatGodBod — interaction and experience design

**Creator:** Babuni.dev.

## A tiny interruption that belongs to the world

WorkThatGodBod takes the practical advice to look away from a screen or move briefly, and wraps it in a miniature adventure. Its current prose is gently theatrical: a player's shoulders may feel like armor, hydration like restoring mana, and a stretch like raising a banner. The aim visible in the README is a low-friction invitation rather than a fitness regimen or nagging scheduler.

The interface is intentionally small. There is no window to keep open: the player chooses action slots and receives a reminder only when a watched button is pressed and the current time/probability gates allow it.

## The player journey

1. Run `/godbod watch` to learn action slot numbers.
2. Use `/godbod slot <n>` to add one or several actions; turn watch mode off afterward.
3. Choose a comfortable minimum interval with `/godbod timer` and an occasional response rate with `chance`.
4. Play normally. A qualifying press may select a new prompt from the 99-line pool.
5. Ignore, adapt, or follow it as personally appropriate; `/godbod off` disables reminders.
6. Use `unslot`, `clear` or `info` to adjust the tool.

The only automatically tracked state is the short-term time gate and configured preferences. There is no compliance or personal wellness history.

## An important tension: quiet nudges versus shared messages

The original README describes **“no UI, no nagging”** and implies a gentle interruption. The code in v1.1, however, may broadcast a prompt to nearby players or a social channel. Of qualifying messages, **14%** are routed to GUILD, SAY, YELL, or PARTY. Players not expecting that could see it as embarrassing or disruptive, and other participants did not request a reminder.

This tension is a real design question, not a historical motive we can assign from the source. The previous v0.2 output routing even included general/world channels; v1.1 explicitly removed those routes but kept limited sharing. **No local-only preference is implemented in v1.1.**

## Tone and accessibility

Prompts are imaginative and usually concise. They cover sitting and standing, arm/leg movement, eye breaks, breathing and hydration. Some mention balance with eyes closed, neck motion or higher-effort exercises. The addon cannot judge someone's needs or safety. Readers should understand these as optional suggestions, never obligations or health advice.

Potential future design improvements—user choice of local-only output, a “skip movements” filter, shorter chat copy, and clearer notification of public sending—belong in the roadmap as **proposals**, not unapproved changes.

## No category selector

Although the writing falls into recognizable themes, the source uses one flat `EXERCISES` list and selects uniformly across it. “Hydration,” “movement,” and “posture” are editorial content tags, not implemented filtering options.
