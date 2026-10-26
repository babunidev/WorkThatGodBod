# WorkThatGodBod — technical architecture v1.1

**Source:** `WorkThatGodBod.lua` and `.toc` on 2026-10-26. **Static source inspection only**, no WoW execution.

## Control flow

```text
Player presses an action bar slot
  -> replaced global UseAction(slot, checkCursor, onSelf)
     -> GOD_LoadOnce() binds the character's saved config
     -> if watchMode, print the slot locally
     -> if slot exists in GOD.slots:
          -> GOD_Trigger(GetTime())
             -> enabled?
             -> enough seconds since GOD.last?
             -> set GOD.last = now
             -> math.random(1,100) <= GOD.chance?
                -> pick one of 99 EXERCISES
                -> outputExercise(text)
                   -> 86% local
                   ->  4% GUILD
                   ->  2% SAY
                   ->  2% YELL
                   ->  6% PARTY
     -> call captured _Orig_UseAction(slot, checkCursor, onSelf)
```

The original button is delegated after the attempt. No check of spell success, combat state or whether the suggested movement was performed. The addon has no repeating update loop, so its named `timer` value is an interval between eligible **action-driven attempts**, not a continuously ringing alarm.

## Source structure

- **`EXERCISES`:** a flat table of **99 different prompt strings**. `U.pick` selects uniformly using `math.random(1, n)`.
- **`U` helpers:** `trim`, `upper`, `split_cmd` using `string.find`, and `pick`.
- **`charKey()`:** joins `UnitName("player")` with `GetRealmName()` (fallbacks if absent).
- **`GOD` table:** bound character configuration (`db`, `slots`, `timer`, `chance`, `enabled`), unsaved `watchMode`, unsaved `last` (initially `0`), plus `_loaded`.
- **`outputExercise()`:** chooses a chat destination; it does not verify eligibility for guild/party messaging or fall back locally after a failed send.
- **Slash handler:** `/godbod` with nine case-insensitive commands: `slot`, `unslot`, `clear`, `watch`, `chance`, `timer`, `on`, `off`, `info`.

## Configuration/persistence

The TOC has `## SavedVariables: WorkThatGodBodDB` (account-wide). Lua uses:

```text
WorkThatGodBodDB
└── chars
    └── "<character-name>-<realm-name>"
        ├── slots       -- table: slot ID => true
        ├── timer       -- default 60 seconds
        ├── chance      -- default 100
        └── enabled     -- default true
```

`GOD_LoadOnce` is called on a `UseAction` press or slash command, creating the current character record when needed. `PLAYER_LOGIN` seeds `math.random`. `PLAYER_LOGOUT` writes values back **if `GOD.db` has already been bound**, avoiding a write from an uninitialized per-character record.

Because settings reside inside an account-level table under distinct character keys, “per-character” refers to **application-level separation**, not the TOC's `SavedVariablesPerCharacter` mechanism.

## Output distribution — read the condition, not the comment

| `math.random(1,100)` outcomes | Path | Calculated share |
| --- | --- | ---: |
| 1–86 | `godChat` local | 86% |
| 87–90 | `SendChatMessage(..., "GUILD")` | 4% |
| 91–92 | `... "SAY"` | 2% |
| 93–94 | `... "YELL"` | 2% |
| **95–100** | `... "PARTY"` | **6%** |

The nearby comment says “95-96 /party”; that comment is **inaccurate** because the actual code compares `roll >= 95`. These percentages are conditional on an emote/prompt actually being produced. Invalid group/party state can affect delivery. No code-level route to general/world channels remains in v1.1.

## Remaining source-level edge cases

- `GOD.last` begins at zero; a first press shortly after entering the game could be suppressed if `GetTime()` is below the configured `timer`.
- Timestamp is advanced **before** the probability roll; a missed roll still consumes the interval.
- `/godbod slot` checks `n >= 1` but does not require an integer or validate legal action IDs; `unslot` accepts any numeric value.
- Wrapper chaining with other add-ons depends on load order and delegation.
- `outputExercise` attempts social sends without explicit player opt-in or destination-failure fallback.
- `math.randomseed` resets the global Lua PRNG state on login.
- Some characters' settings may become inaccessible after renaming or changing realms because they are keyed by name-realm.

These are **source-supported possibilities**, not verified game-client defects.
