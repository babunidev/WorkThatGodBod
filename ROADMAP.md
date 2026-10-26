# WorkThatGodBod — verification and decisions backlog

**Project owner:** Babuni.dev  
**Status:** proposed checks and decisions based on source; no future behavior is approved here.

## Evidence-backed baseline

- v1.1, WoW 1.12.1 / interface 11200, standalone `WorkThatGodBod.lua`.
- **99** distinct prompt strings, sampled uniformly; no categorization at runtime.
- Set of multiple watched slots per character; default 60-second cooldown, 100% probability, enabled.
- Account-wide `WorkThatGodBodDB` subdivided by player name and realm.
- Reminders routed 86% local, 4% guild, 2% say, 2% yell, 6% party **when a prompt is produced**.
- No automated tests are present in the inspected repository.

## Priority 1 — verify existing client behavior

1. Install exactly the committed addon on its intended Vanilla 1.12-compatible client; verify Lua/TOC parsing and command registration.
2. Use `/godbod watch` to discover slots; add several, remove one with `unslot`, clear all with `clear` and confirm both triggering and persisted state.
3. Test `/godbod timer` boundaries and `chance 0`, `50`, `100`; confirm a failed chance roll still consumes an interval.
4. Verify initial behavior near login because `GOD.last = 0` and the first attempt relies on current `GetTime()`.
5. Confirm enabled/disabled behavior and that the original action is always delegated through `UseAction`.
6. **Test outbound chat routing carefully:** capture local, PARTY, GUILD, SAY and YELL behavior in a controlled group. Verify what happens when no party or guild exists and whether default output can be unexpected to players.
7. Compare actual branching to the current inaccurate in-code comment **“95-96 /party”**: the implementation uses `roll >= 95`, so it covers **95 through 100** (six outcomes).
8. Verify persistence on reload, logout/login, character switch and realm/name key changes.
9. Test output alongside addons also replacing global `UseAction`, without assuming all hooks compose safely.
10. Review potentially uncomfortable movements with appropriate opt-out wording and accessibility feedback; do not state medical effectiveness without evidence.

No step above was executed in a live WoW session for this documentation pass.

## Priority 2 — creator choices (not authorized changes)

- Should **local-only** be the default or an explicit toggle, with any social-chat output opt-in?
- Should guild/party/say/yell sending be retained at all?
- Should prompt frequency measure time since an actual **display**, or time since the last **eligible attempt**, as it does today?
- Should players choose categories or exclude certain physical activities, even though the original concept favored full random selection?
- Should the software offer more accessible, lower-intensity suggestions?
- Should the plugin include a clear in-game statement that it may send messages to other players?

Any decisions require Babuni.dev's explicit answer. This review made no gameplay change.

## Verification record format

For each test, record the exact client version, loaded addons, character situation, steps, expected versus actual result, timestamps/screenshots/logs where appropriate, and commit tested. Do not mark “works” on a static source reading.
