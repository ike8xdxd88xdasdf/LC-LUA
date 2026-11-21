# JohnCore v3.2

Ashe · Caitlyn · Corki · Ezreal · Graves · Jinx · Kai'Sa · Katarina · Kayle · Kindred · Kog'Maw · Lulu · Master Yi · Miss Fortune · Orianna · Samira · Senna · Sivir · Tristana · Twisted Fate · Twitch · Viktor · Xerath · Yunara · Zeri · + JohnWalker (universal)

Orbwalker, TobyEvade™, prediction and utility.


---
**Installation is at the bottom. Read the rest first, or you will not get support.**
---

## Before you load
**Disable Maokai R in Evade.** That one is still yours to dodge.

- Load all **4** files from `main scripts/` (`johncore_core.core`, `johncore_evade.core`, `johncore_prediction.core`, `johncore_utility.core`) plus **1** champion file from `champ scripts/` (`johncore_<champion>.core`, or `johnwalker_champ.core` for anyone without a dedicated script).
- **Coming from v2.x:** delete every old `.core` first (`farming_orbwalker.core`, `target_selector.core`, `evade.core`, `prediction.core`, `utility.core`, and old unprefixed champion files). Target selection lives inside `johncore_core.core`. Your menu settings reset once.
- **In LoLcore settings:**
  - Built-in **Evade OFF**. JohnCore walks you out now (`Evade | Lua evade walking`).
  - In **`johncore_core`**, tick **`Use API for onCombo`**, **`Use API for onOrbwalk`** and **`Use API for onCustomLasthit`** (or disable LoLcore's orbwalker). One driver, no fighting over your mouse.

---

## Default keys
| Action | Key | What it does |
| --- | --- | --- |
| Orbwalk / Combo | `Space` | Attack, kite, cast. Everything. |
| Last-hit | `C` | Every last hit, on time |
| Clear (Wave & Jungle) | `V` | Wave and camps, gone |
| Focus enemy target | `Mouse1` | Click him. He's the target now. (`Target selection \| Use mouse1 to focus enemy`) |
| Harass | Unbound (`0`) | Optional toggle/hold in `johncore_core` |
| Toggle evade walking | Unbound (`0`) | Optional quick toggle in `johncore_evade` |

---

## The core (`main scripts/`)
- **`johncore_core.core`**: the engine. Orbwalker, predicted last-hit and waveclear, target selector, gapcloser handling, and the shared engine every champion runs on.
  - `Input | Cursor lock (ms)` (`0–200`, default `0`): a short hold on casts before your cursor comes back. Raise it if fast flicks eat clicks.
  - `Farm | Clear speed (%)` (`0–100%`, default `0%`): `0%` never risks a last hit; toward `100%` it pushes at full attack speed and still takes the last hits first.
  - `Orbwalk | Safety on top of ping ms` (`0–150`, default `0`): raise it if your ping cancels autos.
  - `Orbwalk | Movement vs DPS ms` (`-50–50`, default `0`): negative hits earlier, positive moves more.
  - `Target selection`: `Use mouse1 to focus enemy` & `Use priority list`.
- **`johncore_evade.core`**: path-aware dodging. Walks you out, uses your champion's dash when walking isn't enough, Flash on threat level 5 if you allow it (`Dodge only the most dangerous spells` for a calmer game).
- **`johncore_prediction.core`**: line, circle and dash prediction plus damage modelling. Every script aims with it.
- **`johncore_utility.core`**: Auto Smite (`Dragon`, `Baron`, `Rift Herald`, optional `Void grubs`, `Scuttle Crab`, buffs and camps, `Every monster while an enemy is in range`, `Predict my own hits`). It also runs on its own: Cleanse and QSS on hard CC, item actives (Zhonya's, Locket, Mikael's, Redemption, Randuin's, Rocketbelt, Youmuu's, Shurelya's, Stridebreaker, Gunblade, potions, wards) and summoners (Heal, Barrier, Ignite, Exhaust). Smite keeps working even with the Utility toggle off.

---

## Champions (`champ scripts/`)

### Universal controller
- **`johnwalker_champ.core`**: any champion, no script needed. Orbwalking, last-hitting, clearing, target selection, evade and utility. No champion spells, just clean fundamentals. Steps aside the second a dedicated `johncore_<champion>.core` loads.

### Dedicated champion scripts
- **Ashe** (`johncore_ashe.core`): `Q` & `W` in combat, `Anti-gapclose R` (range slider), manual predicted `R` near cursor (`T`).
- **Caitlyn** (`johncore_caitlyn.core`): isolated `Q` (close-enemy refusal slider), predictive `W` traps + instant `W` on immobilized targets, `E` combat & anti-gapclose, `E W Auto Q Auto` sequence, `Q` waveclear that keeps CS, lethal `R` (`1350+` min distance).
- **Corki** (`johncore_corki.core`): `Q`, `E` and `R` in combat, `R` execute, `W` dash when walking can't dodge.
- **Ezreal** (`johncore_ezreal.core`): predicted `Q` & `W` with timed `W -> Q`, harass mana reserve, `E` escape when walking can't dodge.
- **Graves** (`johncore_graves.core`): `Q` combat (+ fast wall-return filter) & jungle `Q`, `W` on close/casting/CC'd targets or during reload, `E` reload toward cursor + Evade `E`, Dark Harvest `R` execute, semi-manual `E` (`A`) and `R` (`T`).
- **Jinx** (`johncore_jinx.core`): Minigun / Fishbones switching, auto `E` on CC, `E` anti-gapclose (range slider), auto `W` on CC & `W` poke outside AA range on `Space`.
- **Kai'Sa** (`johncore_kaisa.core`): combat spells + `Use R for evade` (lands near a Plasma-marked enemy).
- **Katarina** (`johncore_katarina.core`): dagger combo on `Space`, full all-in after your manual `E` (`W -> Q -> R` + dagger `E`), optional auto `Q` harass and auto dagger `E`.
- **Kayle** (`johncore_kayle.core`): `Q` combo/harass, `E` reset after attack, `E` execute, `E` last-hit & jungle, `W` chase/kite & heal sliders, `R` save under HP % (optional self-only).
- **Kindred** (`johncore_kindred.core`): `Q` weave toward cursor + gapclose + clear + Evade `Q`, `W` uptime, `E` outside windup, `R` self/ally save, stays inside `R`, holds fire under the health floor until `R` ends, jungle `Q`/`W`/`E` (`V`).
- **Kog'Maw** (`johncore_kogmaw.core`): combo `Q` & `W`, `AUTO Q` with no key, `R` execute outside AA range, `R` on CC (`Space`), `R` under HP %, `R` timing after Zhonya's/GA, blended Pred3 + JohnCore prediction.
- **Lulu** (`johncore_lulu.core`): `Q` on `Space`, auto `E` shield for allies & self (threat threshold + `Space`-only toggle), auto `W` on an allied Kog'Maw `W`, `R` anti-gapclose & low-HP save, Superman key (`T`: `W+E`), semi-manual `W` & `E` on ally.
- **Master Yi** (`johncore_masteryi.core`): `Q` on dashes, `Q` dodges danger `4+` & turret shots, jungle `Q` after auto, `W` reset & `W` to tank hard hits, `E` combo & jungle, `R` dangerous-only evade, semi-manual `Q` near cursor (`T`).
- **Miss Fortune** (`johncore_missfortune.core`): `Q`, `W` and `E` in combat.
- **Orianna** (`johncore_orianna.core`): tracks the ball, `Q` from the ball, `W` when enemies reach it, `R` on enemy count or kill, `E` shield on dangerous spells and burst, auto poke key, clear.
- **Samira** (`johncore_samira.core`): `Q` combat & auto `Q` on champions, `Q` waveclear that keeps CS, `W` spin & projectile block, `E` chain & gapclose, `R` at S grade, melee magnet (`< 200`).
- **Senna** (`johncore_senna.core`): `Q` through aligned units, `Q` ally heal toggle, heal key (`H`), `W` with collision, predicted `R` execute (idle execute & margin slider), auto soul pickup.
- **Sivir** (`johncore_sivir.core`): combat spells + `E` spell shield on dangerous spells instead of dodging.
- **Tristana** (`johncore_tristana.core`): `Q` Rapid Fire, `E` bomb in range, `R` execute counting bomb stacks + the follow-up auto (margin & overshoot sliders), `Anti-gapclose R`.
- **Twisted Fate** (`johncore_twistedfate.core`): auto Gold card on `Space`, Gold card on `R` before the teleport, card keys: Gold (`W`), Red (`T`), Blue (`E`), `Q` on stunned/slowed targets.
- **Twitch** (`johncore_twitch.core`): `W` & `E` in combat, `E` execute, harass mana reserve.
- **Viktor** (`johncore_viktor.core`): `Q` with the empowered auto, `E` laser on the best line, `W` trap only when they can't walk out, `W` anti-gapclose, `R` on kill or hard CC, semi-manual `E` (`T`).
- **Xerath** (`johncore_xerath.core`): `Q` charge release on aligned targets (+ `Prediction %` & charge deadline), center `W` + waveclear `W` (`minimum minions hit`), `E` on dashes, Artillery `R` key (`T`) on `Target selector` or `Closest to cursor`.
- **Yunara** (`johncore_yunara.core`): `Q` in range, predicted `W` between autos, `E` while moving & fleeing, `R` on `Space`, Evade `R + E` on level-5 danger, flee key.
- **Zeri** (`johncore_zeri.core`): semi-manual predicted `W` (`H`), direct `W` in combat, harass mana reserve, `E` escape when walking can't dodge, `Q` on turrets in push (`V`), `Q` weaving & charged attacks.

---

## How to install the `.core` files
1. Download all files from `main scripts/` and your champion from `champ scripts/`.
2. Delete any old v2.x `.core` files (`farming_orbwalker.core`, `target_selector.core`, `evade.core`, `prediction.core`, `utility.core`, old unprefixed champion files).
3. Copy the 4 files from `main scripts/` and your champion file into your LoLcore scripts folder and load them.
4. Built-in **Evade** off. In **`johncore_core`** tick **`Use API for onCombo`**, **`Use API for onOrbwalk`** and **`Use API for onCustomLasthit`**.

Then hold Space.

<img width="387" height="261" alt="image" src="https://github.com/user-attachments/assets/74371ebd-09fd-45e1-b850-b2f5f93caae5" />
