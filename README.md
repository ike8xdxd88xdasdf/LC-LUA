# JohnCore v2.1 — LolCore scripts (beta build)

**Ashe · Caitlyn · Jinx · Kai'Sa · Kog'Maw · Lulu · Miss Fortune · Samira · Senna · Sivir · Tristana · Twitch · Xerath · Yunara · Zeri**

One shared core: an orbwalker, evade, prediction, target selector and utility. Every champion script runs on top of it. You get one consistent orbwalker and evade, whichever champion you play.

---
**Scroll to bottom for tutorial on how to install the .core files**
---

## Be aware

1. **Load the 5 core scripts plus 1 champion script, all at once, in the loaded folder.** Use only the files from the latest release. Double and triple check before starting LolCore.
   - Core: `farming_orbwalker`, `target_selector`, `evade`, `prediction`, `utility`
   - Champion: the one you play, for example `jinx` or `xerath_1`
2. **Check your key bindings in the API tab on every reload** (config saving is coming soon).
3. **In LolCore, turn off:**
   - Main: Orbwalker Clicking, Prediction and Evade.
   - Hero: everything.
   **In LolCore, turn on:**
   - Target Mode -> priority list (We can prioritize targets, our target_selector works together with this. If you don't want priority list, leave all on priority 3 = default)
4. **Right-clicking to move by hand can work against evade.**
5. **Autos getting cancelled?** Raise `Orbwalk | Safety on top of ping ms` (default 25). Your ping is read automatically; this is only the extra safety on top.
6. **Game resolution different from your monitor resolution?** Issues might occur. 
7. **Game resolution above 1080p?** Issues might occur.
8. **Keep mouse speed in LoL at 50 for accurate aiming in LolCore**

---

## Default keys

| Key | What it does |
|---|---|
| **Space** | Orbwalk and fight (autos and spells) |
| **C** | Last hit |
| **V** | Wave clear / push |
| **Harass** | Unbound, set it in the menu |
| **Left click (mouse1)** on an enemy champion | Focus that enemy. Left click elsewhere to clear it |
| **Toggle evade walking** | Unbound, set it in the menu |

Champion keys (T, H, W/E) are listed under each champion.

---

## Core features (every champion)

### Orbwalker
- **Moves the moment the attack windup ends**, so it doesn't stand still after an auto or cancel one.
- **Keeps auto-attacking while rooted or silenced.**
- **Self-buffs never delay an auto** (Tristana Q, Yunara Q, Kog'Maw W, Jinx swaps).
- **Weaves spells between autos**, and walks first when a spell would make you stand still.
- **Farming:**
  - Last hit (C) and push (V), with health prediction.
  - It doesn't steal a minion your spell is already killing.
  - Jungle monsters are cleared without stalling.

### Evade 
- **Walks out of skillshots** from a custom dodge list. *Lua evade walking* is **on** by default; turn off the game's own evade first.
- **Ignores spells that can't reach you.** A Thresh, Blitz or Morgana Q blocked by a minion or champion in between is not dodged.
- **Uses a dash** (Ezreal E, Zeri E, Kai'Sa R, etc) when walking can't escape.
- **Flash:** allowed for level 5 spells, with the *Allow Flash for enemy threat level 5* box.

**How to set up evade with Flash:**
1. Enable *Lua evade walking* and *Allow Flash for enemy threat level 5*.
2. Scroll down in LolCore until you find **Spell threat | (enemy) (spell)**.
3. Set each spell's level:
   - **1:** do not dodge.
   - **2–4:** walk.
   - **5:** Flash when walking is not possible.

*Dodge only the most dangerous spells* limits evade to threat 4–5. We used common sense to rank spells by threat, you can trust us in this.

### Target selector
- **Mouse1 focus is a hard lock:** your spells and autos stay on the focused enemy.
  - When the focus is out of range for an auto or a spell, that auto or spell goes to another champion.
  - Turn it off with *Use mouse1 to focus enemy*.
- **Priority list:** every champion has a built-in priority, with carries first. *Use priority list* turns it on or off.
- **Picks the fastest kill**, and spells prefer your attack target.

### Prediction
- Just werks, or not (send me clips of misses)

### Utility
- **Auto Smite** (epic monsters only by default).

---

## Champions

### Ashe
- **Q and W** in combat.
- **Anti-gapclose R:** R on an enemy whose dash ends within 500 of you (range slider).
- **E for vision:** automatic in combo, when an enemy you are fighting walks out of vision and no ward of yours covers the spot.
- **T:** manual R, predicted at the enemy nearest your cursor.

### Caitlyn
- **Full E → W → Q combo:**
  - E, then the trap goes under their feet;
  - instant W on immobilized targets;
  - Q follows.
- **Q isolated shots.** Q is refused with an enemy closer than 400 (slider), unless Q + 1 auto kills.
- **Automatic lethal R** from at least 1350 distance.
- **E anti-gapclose.**

### Jinx
- **Automatic minigun ↔ rockets:**
  - rockets when an enemy champion is inside rocket range (+125 in combo), from minigun range minus 100;
  - back to minigun at minigun range minus 150;
  - rockets for splash on 2+ grouped champions;
  - farm modes never swap.
- **W:**
  - poke on Space when the enemy is outside auto range;
  - automatic W on a crowd-controlled enemy outside auto range.
- **E:**
  - automatic E on crowd-controlled enemies;
  - anti-gapclose E in combo, on an enemy within 300 (slider) or dashing at you.
  - The chompers go in front of them, further when they walk at you.

### Kai'Sa
- **Q** in combat.
- **W** only at an enemy who can't move when it lands, or when W (with its Plasma rupture) kills.
- **Use R for evade:** R to a spot near a Plasma-marked enemy when walking can't escape. It learns your R dash speed from your own R casts.

### Kog'Maw (experimental)
- **Q:**
  - automatic Q without a key (hit chance and mana sliders);
  - Q in combo between autos.
- **W** in combo when in range.
- **R:**
  - automatic R for kills outside auto range (hit chance and safety margin sliders);
  - R right after Guardian Angel or Zhonya's.

### Lulu
- **Superman key (T, hold):** W, then E, on your superman ally. Pick the ally with the *Superman target* boxes.
- **Semi-manual W / E (W / E keys):** the script picks the ally. Use them with your cursor on empty ground, because the game also gets the key.
- **Automatic:**
  - **E** shields allies and you when damage is about to land (threat-level slider);
  - **W** on an allied Kog'Maw when he uses his W;
  - **R** knocks up enemies that dash in, or saves a low ally (below 20%);
  - *Allow R on yourself*; optional R on enemies that walk in.

### Miss Fortune
- **Q, W and E** in combat, timed between autos.

### Samira
- **Full combo chain:** W spin → E through the target → Q → R at S grade.
- **W blocks incoming projectiles.**
- **E gap close** when the target is out of auto range.
- **Auto Q** on enemy champions, no key needed.

### Senna
- **Auto collects souls** (orb keys only).
- **Q:**
  - in combo and harass;
  - through aligned units beyond your target's range;
  - heals allies in combat (option).
- **H:** Q heal key.
- **W** prediction with collision.
- **R:** predicted execute during combat (damage margin slider). Optionally also without the combat key.

### Sivir
- **Q and W** in combat.
- **Automatic E spell shield** on dangerous spells (the evade list) that would really hit you, instead of dodging them. It takes blocking minions into account.
- Harass mana reserve slider.

### Tristana
- **Enable Q:** Q never delays an auto or the move after it.
- **Enable E:** E bombs your attack target.
- **R:**
  - lethal execute with bomb + follow-up auto;
  - **Anti-gapclose R** on enemies dashing in.
- **W is fully manual**, so you decide where you jump.

### Twitch
- **W and E** in combat.
- **E execute** during combat.
- Harass mana reserve slider.

### Xerath
- **Hold Space:** W and E. W prefers to hit the centre.
- **Q:** press Q once and the script aims and releases it on an aligned target. It also fires before the charge runs out.
- **R:** press R to enter R mode, then **hold T** to shoot.
  - *Champion / R | Target selection:* target selector, or closest to cursor.
- **W wave clear** (3+ minions).

**Recommended:**
1. In League, enable **manual cast Q** (click once to charge, click again to release).
2. Bind the Lua orbwalker to **Space**. This can fix buggy spell shooting when Space is pressed while a hit is resolving.
3. If Q overshoots (predicts too far), lower *Q Prediction %*.

### Yunara
- **Q:** Cultivation of Spirit in attack range.
- **W:** predicted between attacks (prediction 50%, slider).
- **E:** Kanmei Steps while moving and fleeing.
- **R:** Transcend in attack range on Space.
- **Evade:** R + E for level 5 spells when Flash is down.
- **Flee key:** unbound, set it in the menu.

### Zeri
- **Q fires on cooldown,** also during R (chain lightning ignores minions in the way).
- **Farming:** Q in last hit and push. Autos only finish kills.
- **Autos at champions only when charged.** Charged zaps are weaved in attack range.
- **Q on turrets** in push mode.
- **E as evade** when walking can't escape.
- **H:** semi-manual W (predicted target). Direct W in combat is off by default.

---

## Feedback

This is a beta. When something feels off, tell me:
- the champion;
- what you were doing (combo, farming, evading);
- what happened.

A clip helps a lot.

<img width="387" height="261" alt="image" src="https://github.com/user-attachments/assets/74371ebd-09fd-45e1-b629-e4ff71bc15ca" />
