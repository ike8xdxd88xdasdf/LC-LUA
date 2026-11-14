# JohnCore v2.3 — LoLcore scripts

Ashe · Caitlyn · Ezreal · Graves · Jinx · Kai'Sa · Kayle · Kindred · Kog'Maw · Lulu · Master Yi · Miss Fortune · Samira · Senna · Sivir · Tristana · Twisted Fate · Twitch · Xerath · Yunara · Zeri · + JohnWalker (universal)

One shared core: orbwalker, evade, prediction, and utility. 

---
**Scroll to the bottom for installation steps for the `.core` files.**
---

## Be aware
- Load all **4** files from `main scripts/` (`johncore_core.core`, `johncore_evade.core`, `johncore_prediction.core`, `johncore_utility.core`) plus **1** champion file from `champ scripts/` (`johncore_<champion>.core`, or `johnwalker_champ.core` for any champion without a dedicated script).
- **Upgrading from v2.1:** Delete all old v2.1 `.core` files (`farming_orbwalker.core`, `target_selector.core`, `evade.core`, `prediction.core`, `utility.core`, and old unprefixed champion `.core` files). Target selection is now built into `johncore_core.core`. Saved menu settings reset once with the new `johncore_*` script names.
- **In LoLcore settings:**
  - Turn built-in **Evade OFF** (`Evade | Lua evade walking` handles dodging).
  - In **`johncore_core`**, tick **`Use API for onCombo`**, **`Use API for onOrbwalk`**, and **`Use API for onCustomLasthit`** (or disable LoLcore's built-in orbwalker) so only JohnCore issues orbwalk and last-hit inputs.

---

## Default keys
| Action | Key | Notes |
| --- | --- | --- |
| Orbwalk / Combo | `Space` | Attack, kite, and run champion combat spells |
| Last-hit | `C` | Last-hit minions cleanly |
| Clear (Wave & Jungle) | `V` | Waveclear and jungle clear |
| Focus enemy target | `Mouse1` | Left-click to prioritize an enemy (`Target selection \| Use mouse1 to focus enemy`) |
| Harass | Unbound (`0`) | Optional toggle/hold key in `johncore_core` |
| Toggle evade walking | Unbound (`0`) | Optional quick toggle in `johncore_evade` |

---

## Core features (`main scripts/`)
- **`johncore_core.core`** — Orbwalker, predicted last-hit & waveclear, target selector, gapcloser library, and shared marksman engine.
  - `Input | Cursor lock (ms)` (`0–200`, default `0`): brief mouse hold window on casts/inputs before returning to your cursor.
  - `Farm | Clear speed (%)` (`0–100%`, default `0%`): `0%` preserves strict last-hit safety windows; raising toward `100%` reduces wait windows toward full attack-speed pushing while still catching immediate last hits first.
  - `Orbwalk | Safety on top of ping ms` (`0–150`, default `25`): raise slightly if high ping cancels autos.
  - `Target selection`: `Use mouse1 to focus enemy` & `Use priority list`.
- **`johncore_evade.core`** — Path-aware skillshot dodging (`Lua evade walking`, `Dodge only the most dangerous spells`, optional `Allow Flash for enemy threat level 5`).
- **`johncore_prediction.core`** — Shared linear/circular/dash prediction engine and damage modeling.
- **`johncore_utility.core`** — Auto Smite (`Dragon`, `Baron`, `Rift Herald`, optional `Void grubs`, `Scuttle Crab`, jungle buffs/camps, `Every monster while an enemy is in range`, `Predict my own hits`). Auto Smite stays active even if the general Utility toggle is turned off.

---

## Champions (`champ scripts/`)

### Universal controller
- **`johnwalker_champ.core`** — Works on any champion without a dedicated script. Provides shared orbwalking, last-hitting, clearing, target selection, evade, and utility (no champion spells). Automatically yields whenever a dedicated `johncore_<champion>.core` script is loaded.

### Dedicated champion scripts
- **Ashe** (`johncore_ashe.core`): `Q` & `W` in combat, `Anti-gapclose R` (with range slider), manual predicted `R` near cursor (`T`).
- **Caitlyn** (`johncore_caitlyn.core`): Isolated `Q` (with close-enemy refusal slider), predictive `W` traps + instant `W` on immobilized targets, `E` combat & anti-gapclose, `E W Auto Q Auto` combo sequence, `Q` waveclear (preserve CS), automatic lethal `R` (`1350+` min distance).
- **Ezreal** (`johncore_ezreal.core`): Predicted `Q` & `W` with timed `W -> Q` follow-up, harass mana reserve slider, `E` evade escape when walking cannot dodge.
- **Graves** (`johncore_graves.core`): `Q` combat (+ optional fast wall-return filter) & jungle `Q`, `W` on close/casting/CC targets or during reload, `E` reload toward cursor in combat/lane clear + Evade `E`, Dark Harvest `R` execute calculation, semi-manual `E` (`A`) and semi-manual `R` (`T`).
- **Jinx** (`johncore_jinx.core`): Automatic Minigun / Fishbones switching, Auto `E` on CC, `E` anti-gapclose (with range slider), Auto `W` on CC & `W` poke outside AA range on `Space`.
- **Kai'Sa** (`johncore_kaisa.core`): Combat abilities + `Use R for evade` (escape landing near a Plasma-marked enemy).
- **Kayle** (`johncore_kayle.core`): `Q` in combo/harass, `E` auto-reset after attack, `E` execute, `E` last-hit & jungle clear, `W` chase/kiting & ally/self heal sliders, `R` save under HP % (optionally self-only).
- **Kindred** (`johncore_kindred.core`): `Q` weave after windup toward cursor + gapclose + clear + Evade `Q` dodge, `W` uptime, `E` outside windup, `R` self/ally save, stay inside `R`, hold autos/skills under health floor until `R` ends for burst, jungle clear `Q`/`W`/`E` (`V`).
- **Kog'Maw** (`johncore_kogmaw.core`): Combo `Q` & `W`, standalone `AUTO Q` (no key), `R` lethal execute outside AA range, `R` on CC (`Space`), `R` under HP % / non-lethal outside AA range, post-Zhonya/GA `R` timing, blended Pred3 + JohnCore prediction.
- **Lulu** (`johncore_lulu.core`): `Q` combat (`Space`), Auto `E` shield for allies & self (configurable threat threshold + `Space`-only toggle), Auto `W` on allied Kog'Maw `W`, `R` anti-gapclose knockup & low-HP save, Superman key (`T` — `W+E`), semi-manual `W` (`W`) & `E` (`E`) on ally.
- **Master Yi** (`johncore_masteryi.core`): `Q` gapclose on dashing enemies, `Q` dodge dangerous spells (`4+`) & turret shots, jungle `Q` after auto, `W` auto reset (min saved ms slider) & `W` mitigation for hard spells/turret shots, `E` combo & jungle clear, `R` dangerous-only evade, semi-manual `Q` near cursor (`T`).
- **Miss Fortune** (`johncore_missfortune.core`): `Q`, `W`, and `E` in combat.
- **Samira** (`johncore_samira.core`): `Q` combat, Auto `Q` on enemy champions, `Q` waveclear (preserve CS), `W` spin & projectile block, `E` combo chain & gapclose, `R` at S grade in range, melee stick-to-target magnet (`< 200` range).
- **Senna** (`johncore_senna.core`): `Q` combat & extended `Q` through aligned units, `Q` ally heal toggle, manual `Q` heal key (`H`), `W` prediction with collision, predicted `R` execute (optional idle execute & margin slider), auto soul collection on orb keys.
- **Sivir** (`johncore_sivir.core`): Combat spells + `E` spell shield on dangerous spells instead of dodging.
- **Tristana** (`johncore_tristana.core`): `Q` Rapid Fire in combat, `E` bomb in attack range, `R` lethal execute factoring bomb stacks + follow-up auto (with margin & overshoot sliders), `Anti-gapclose R`.
- **Twisted Fate** (`johncore_twistedfate.core`): Auto Gold card in combo (`Space`), auto Gold card on `R` (Destiny) before teleport, semi-manual card keys — Gold (`W`), Red (`T`), Blue (`E`), `Q` on stunned/slowed targets.
- **Twitch** (`johncore_twitch.core`): `W` & `E` in combat, `E` execute, harass mana reserve slider.
- **Xerath** (`johncore_xerath.core`): Manual `Q` charge release on aligned targets (+ `Prediction %` & charge deadline fallback), predictive center `W` + lane waveclear `W` (`minimum minions hit`), observed dash prediction (`E`), Artillery `R` key (`T`) with `Target selector` / `Closest to cursor` mode.
- **Yunara** (`johncore_yunara.core`): `Q` Cultivation of Spirit in range, predicted `W` between autos (`Prediction percent` slider), `E` Kanmei Steps while moving & fleeing, `R` Transcend on `Space`, `Evade` `R + E` fallback for level-5 danger, configurable Flee key.
- **Zeri** (`johncore_zeri.core`): Semi-manual predicted `W` (`H`), optional direct `W` in combat, harass mana reserve slider, `E` evade escape when walking cannot dodge, `Q` on turrets in push mode (`V`), `Q` weaving & charged attack handling.

---

## How to install the `.core` files
1. Download all files from `main scripts/` and the champion file(s) you want from `champ scripts/`.
2. Remove any old v2.1 `.core` files (`farming_orbwalker.core`, `target_selector.core`, `evade.core`, `prediction.core`, `utility.core`, or old unprefixed champion `.core` files).
3. Copy the 4 files from `main scripts/` and your chosen `champ scripts/*.core` file(s) into your LoLcore scripts folder and load them in LoLcore.
4. Disable LoLcore's built-in **Evade**, and inside **`johncore_core`** tick **`Use API for onCombo`**, **`Use API for onOrbwalk`**, and **`Use API for onCustomLasthit`**.

<img width="387" height="261" alt="image" src="https://github.com/user-attachments/assets/74371ebd-09fd-45e1-b850-b2f5f93caae5" />
