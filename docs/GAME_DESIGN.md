# PITFALL LEGION — Game Design Document

*A high-polish mobile ball-launcher roguelite in the spirit of Ball x Pit.*

---

## 1. High Concept

**One-line pitch:** You stand at the bottom of a cursed pit. Monsters descend in
waves from above. You auto-fire bouncing balls that shred them — and every run,
you level up, **fuse balls into wild hybrids**, and face a screen-filling boss
before descending deeper.

**Genre:** Brick-breaker × bullet-heaven roguelite (portrait, one-hand play)

**Session length:** 5–12 minute runs, 30-second "one more run" restart loop.

**Why it works on mobile:**
- One-thumb aiming; auto-fire does the busywork.
- Runs fit a commute; meta progression rewards every run, even failures.
- The fusion system creates "I want to see what THAT combo does" pull.

---

## 2. Core Loop

```
AIM (drag thumb) → balls auto-fire and bounce → enemies descend row by row
   → collect XP gems → LEVEL UP: pick 1 of 3 balls/upgrades
   → fuse two max-level balls into a hybrid → BOSS at depth milestones
   → die or clear → spend meta-currency in the Camp → next run is different
```

### The pit
- Portrait screen. Player character locked at bottom; enemies spawn at top and
  march down in loose rows. If an enemy touches the player line, it deals damage
  to your HP bar (no instant death — dramatic close calls instead).
- Balls fire upward automatically at your aim angle, bounce off walls and
  enemies. Each ball is a distinct entity with its own element/behavior.
- **Depth = progress.** The pit background scrolls; every 10 "meters" the biome
  shifts (Catacombs → Fungal Caves → Magma Core → The Rift), enemies re-skin
  and get new behaviors, music layers intensify.

### Controls (one thumb, zero tutorial needed)
- Hold anywhere: an aim line appears with a bounce preview (first 2 bounces).
- Release does nothing — firing is continuous. Moving your thumb steers.
- Double-tap: trigger your charged **Ultimate** (see §5).
- That's it. Everything else is menus between waves.

---

## 3. Ball Arsenal (the "power ups")

Balls are the build system. You start each run with 1 basic ball; level-ups add
more or upgrade existing ones (max Lv5). The screen caps at ~7 ball types but
each type fires multiple projectiles at higher levels.

### Tier 1 — Base balls (pick-ups during runs)

| Ball | Behavior |
|---|---|
| **Iron** | Plain damage, high fire rate. The workhorse. |
| **Ember** | Ignites enemies; burning enemies take damage over time and glow. |
| **Frost** | Slows enemies 30%; frozen enemies shatter for AoE on death. |
| **Volt** | Chains lightning to 2 nearby enemies per hit. |
| **Venom** | Poison stacks; poisoned enemies drop double XP gems. |
| **Stone** | Slow, huge, pierces through a full column of enemies. |
| **Phantom** | Passes through enemies, damaging everything on its path, bounces only on walls. |
| **Blade** | Ricochets extra times; +damage per bounce this volley. |
| **Leech** | Heals you for a % of damage dealt. |
| **Gravity** | On hit, briefly pulls nearby enemies together (combo enabler). |
| **Mirror** | Splits into 2 on first wall bounce. |
| **Anchor** | Sticks to an enemy and pulses AoE damage for 3s. |

### Tier 2 — Fusions (the magic moment)
When you own two balls at max level, the next level-up offers a **Fusion**.
Fusions consume both parents and are dramatically stronger and visually loud.
Examples (any elemental pair should have a designed result — aim for 25+ at launch):

| Fusion | Parents | Behavior |
|---|---|---|
| **Steam Engine** | Ember + Frost | Leaves a drifting steam cloud that damages and blinds (enemies inside stop advancing). |
| **Plasma Orb** | Ember + Volt | Slow-moving sun that continuously zaps everything near its path. |
| **Toxic Storm** | Venom + Volt | Chain lightning spreads poison stacks between enemies. |
| **Black Hole** | Gravity + Phantom | Periodically spawns a vortex that sucks in a whole row, then detonates. |
| **Guillotine** | Blade + Stone | Massive sawblade that grinds down a column then falls back through it. |
| **Vampire Court** | Leech + Mirror | Splitting heal-balls; overheal converts to a shield. |
| **Frostbite Anchor** | Frost + Anchor | Freezes a whole area solid; shatter chain-reacts. |
| **Wildfire** | Ember + Mirror | Every split spreads ignite; fills the screen with cinders. |

Design rule: **every fusion must be readable at a glance** — unique silhouette,
color, sound, and a one-time "fusion cutscene" flash (0.6s slow-mo, name card,
haptic thump) the first time you create it. That moment is the game's shareable
screenshot.

### Passive relics (level-up alternatives)
Fire rate, ball speed, ball size, +1 bounce, crit chance, XP magnet radius,
"wall bounces deal damage," "first hit each volley crits," HP/armor, gem value.
Passives keep level-up choices interesting when you don't want a new ball.

---

## 4. Enemies

March-down grid with personality. Every enemy telegraphs what it does by
silhouette alone.

- **Shambler** — basic walker. Fodder that makes your build feel strong.
- **Crab** — armored front; must be hit from behind via wall bounces (teaches ricochet play).
- **Winged Imp** — descends in a sine wave, faster than the rows.
- **Broodmother** — slow; splits into 4 Shamblers on death (AoE check).
- **Shieldbearer** — projects a shield over enemies behind it; kill first.
- **Necromancer** — stays high, revives dead rows until sniped (accuracy check).
- **Tunneler** — burrows, invulnerable, surfaces two rows lower.
- **Berserker** — enrages and sprints when below half HP.
- **Cursed Bell** — doesn't attack; if it reaches the bottom it silences a random ball for 20s. Priority-target tension.
- **Mimic Chest** — looks like a loot drop; bites. Drops big rewards.

Elite variants (random modifiers): *Volcanic* (drops lava on death), *Gilded*
(double gems, double HP), *Phasing* (blinks every 3s), *Vampiric* (heals allies).

---

## 5. Bosses

A boss every 25 meters. Bosses **enter the pit from above and take over the
whole screen** — the wave grid stops, music swaps to a boss theme, and a name
banner slams in with haptics. Every boss has 3 phases at 100/60/25% HP and at
least one mechanic that interacts with *bouncing* (the core verb).

### Boss roster (launch: 6)

1. **GRUNDEL, THE PIT MOUTH** (Catacombs, first boss)
   A giant mouth spanning the pit floor-to-wall. Phase 1: chomps at your balls —
   swallowed balls are gone for 5s, so you aim around his bite rhythm. Phase 2:
   spits swallowed balls BACK as hazards you must dodge with your aim line
   (your own build weaponized against you). Phase 3: gapes wide — throat is a
   weak point behind chomping teeth. Teaches timing.

2. **THE COLLECTOR** (Catacombs alternate)
   A hunched hoarder with a sack. Steals your XP gems off the floor; every 10
   gems stolen he grows and hits harder. Kill him to get everything back with
   interest. Creates a real economy panic. Weak point: the sack — hitting it
   spills gems and stuns him.

3. **MADAME MYCELIA** (Fungal Caves)
   A fungal queen who covers the walls in bounce-absorbing moss (balls stop
   ricocheting!). She spawns puffball turrets that lob spore arcs. You must
   shoot moss off the walls to restore your bounces, then punish her. Phase 3:
   she splits into 3 clones — only the one that casts spores is real.

4. **KNIGHT OF CHAINS** (Fungal Caves alternate)
   Armored duelist who descends on a chain and swings across the pit like a
   pendulum. Blocks frontal hits with his shield; only back-hits (wall-bounce
   angles) damage him. Phase 2: throws chain hooks that drag your character
   left/right, forcibly changing your firing position. Phase 3: armor shatters,
   he goes berserk-fast. The "mastery of ricochet" exam.

5. **CINDERWYRM** (Magma Core)
   A lava serpent that coils around the *outside* of the pit and pokes head/tail
   segments through the walls. Body segments plate over time — frost balls crack
   plating instantly (build-check with counterplay: heavy hits also work,
   slower). Phase 3: floods the bottom third with rising lava — your safe zone
   shrinks and enemies keep descending. DPS race with real stakes.

6. **THE ARCHITECT** (The Rift, final launch boss)
   A geometry god who **rebuilds the pit around you**: rotates wall segments,
   adds bumpers and one-way gates, turns the arena into a pinball machine — and
   the bumpers supercharge your balls (+damage per bumper hit), so the hazard is
   also your best weapon. Phase 3: he mirrors YOUR build, firing your own
   fusion balls down at you. Final exam on everything.

### Boss polish checklist (every boss, no exceptions)
- Unique intro: 1.5s cinematic slide-in, name banner, screen shake, bass hit.
- Health bar with phase notches; phase transitions have a 0.5s slow-mo.
- Distinct silhouette + 2-frame telegraph before every attack.
- Weak-point hits: louder crunch, bigger numbers, different hit-spark color.
- Death: multi-explosion cascade, slow-mo, gem fountain, "DEPTH CLEARED" card.
- Post-boss: guaranteed choice of 1-of-3 **rare** relics.

---

## 6. Meta Progression — The Camp

Between runs you return to a small camp at the pit's rim that **visibly grows**:

- **Forge** — permanent stat upgrades (spend Scrap): HP, base damage, starting ball level, gem magnet, revive charge.
- **Bestiary** — kill milestones per enemy grant +5% damage vs. that enemy; boss entries replay their intro cinematics.
- **Ball Codex** — collection screen; discovering a fusion unlocks it as a *rare random offer* in future runs even without both parents.
- **Characters** — unlockable launchers with different starting balls and one unique passive (e.g., the Alchemist starts with Venom and brews a free potion each boss; the Warden's walls deal contact damage).
- **Expeditions (idle hook)** — send an unlocked character down a cleared depth; return in 4–8h with Scrap. Respectful idle layer, no timers gating core play.
- **Daily Rift** — fixed-seed daily run with a mutator ("all balls are Mirror," "double bosses"), global leaderboard.

---

## 7. The Polish Bible (what "extremely high polished" means)

This is the section that separates a 4.8★ game from a 3.9★ game. Budget real
time for it — roughly **30% of total dev effort**.

### Game feel ("juice")
- **Hit-stop:** 20–40ms freeze on meaty hits, 80ms on crits/kills. The single highest-value trick in the genre.
- **Screen shake:** small directional shake on kills, big radial on explosions/boss slams. Always with an intensity cap and a settings slider.
- **Squash & stretch:** balls stretch along velocity, squash on impact; enemies do a 0.1s squash when hit and pop with a 2-frame white flash.
- **Hit sparks & numbers:** damage numbers with size/color tiers (white → yellow crit → element-colored). Numbers arc outward with gravity, never overlap the aim line.
- **Trails:** every ball has an element-colored trail; fusion balls get layered trails + light glow. Trails alone make screenshots pop.
- **Slow-mo moments:** first fusion creation, boss phase transitions, boss kills, your death (with a "watch your killer celebrate" beat — it makes players laugh instead of rage).
- **Haptics:** light tick per kill (throttled), medium on level-up, heavy pattern on fusion/boss events. Use Core Haptics/`VibrationEffect` patterns, not flat buzzes. Slider in settings.

### Audio
- Adaptive music: base loop + intensity layers keyed to enemy density and depth; dedicated boss themes with phase stems; music ducks 50% for 0.3s on level-up jingle.
- Every ball type has a distinct impact sound family (3–4 round-robin variants, ±5% random pitch) so the mix never turns to static. A global "sounds per 100ms" limiter keeps late-game readable.
- Kill streaks pitch-shift the gem-collect sound up a semitone per gem (Peggle trick — pure dopamine).

### UI/UX polish
- All panels spring-animate (200ms, slight overshoot). Nothing pops instantly.
- Level-up choice cards: staggered deal-in animation, card art, a one-line stat delta ("Volt Lv3 → chains to **3** enemies").
- A ghosted aim line that thickens near the release point; colorblind-safe element palette (shape-coded icons on balls, not just color).
- Run summary screen: damage-by-ball bar chart, depth reached, "new best" callouts, one-tap retry. Retry must be reachable in **<2 seconds** from death.
- 60fps always; every transition interruptible by a tap (never make the player wait).

### Performance & tech polish
- Object pooling for balls/enemies/particles/damage numbers (hundreds of entities; zero runtime allocation in the hot loop).
- Physics on a fixed timestep with interpolation; balls use continuous collision detection (fast balls must never tunnel through walls — a single tunneling bug reads as "broken game").
- Battery mode: optional 30fps + reduced particles.
- Cloud save (platform sync) + local autosave every wave; a run must survive a phone call.

---

## 8. Tech Stack Recommendation

**Engine: Unity (URP, 2D)** — best fit for this scope.
- 2D physics with CCD out of the box, Shader Graph for glow/dissolve effects,
  Burst/Jobs if entity counts spike, mature iOS/Android pipeline, Unity Ads/IAP.
- Alternative: **Godot 4** if avoiding Unity licensing — fully capable for this
  scope, slightly more DIY for mobile services (ads/IAP plugins).
- Avoid web-view stacks (Phaser/Capacitor) — hitting rock-solid 60fps with
  hundreds of physics balls + particles + haptics is exactly where they hurt.

**Architecture notes**
- Balls/enemies as data-driven definitions (ScriptableObjects): a new ball or
  fusion is a data file + art, not code. This is what makes 25+ fusions feasible.
- Deterministic seeded RNG per run → enables Daily Rift and bug repro.
- Status effects (burn/freeze/poison/shock) as a stacking component system so
  fusions compose for free.

---

## 9. Monetization (polish-friendly, no pay-to-win)

- **Premium-lite F2P:** free with a single **"Supporter Pack"** IAP ($6.99) that removes ads forever + a cosmetic trail set.
- Optional rewarded ads only, always player-initiated: revive once per run, double post-run Scrap, one free relic reroll. Never interstitials mid-run.
- Cosmetics: ball skins/trails, character outfits, camp themes. Zero stat impact.
- No energy systems, no timers on core play, no gacha. This is a retention strategy: the genre's audience punishes aggressive monetization with reviews.

---

## 10. Roadmap

| Milestone | Scope | Duration |
|---|---|---|
| **M0 – Feel prototype** | Aim + auto-fire + bounce + 3 balls + 1 enemy + hit-stop/shake/numbers. Goal: the core verb feels great in a graybox. | 2–3 wks |
| **M1 – Vertical slice** | Full run loop: 8 balls, 4 fusions, 6 enemies, Grundel boss, level-up flow, death → retry. | 4–6 wks |
| **M2 – Meta & content** | Camp, Forge, 12 balls / 12 fusions, 3 biomes, 4 bosses, 2 characters, save/cloud. | 8–10 wks |
| **M3 – Polish pass** | Full audio, haptics, adaptive music, UI animation pass, perf/battery, colorblind, localization-ready. | 4–6 wks |
| **M4 – Soft launch** | 1–2 test markets, analytics (D1/D7 retention, run length, fusion discovery rate), tune difficulty curve. | 4 wks |
| **Launch + LiveOps** | Daily Rift live, +2 bosses, seasonal mutators, new fusion drops monthly. | ongoing |

**Success metrics to tune toward:** D1 retention >40%, median session >2 runs,
≥70% of players discover a fusion in their first 3 runs (if not, surface fusion
offers earlier — it's the hook).

---

## 11. First Playable — Next Steps in This Repo

1. Decide engine (recommend Unity URP 2D as above).
2. Build M0 graybox: one scene, thumb-aim, pooled balls, one enemy row spawner.
3. Tune the juice trifecta (hit-stop, shake, damage numbers) before adding ANY content — if graybox isn't fun, content won't save it.
4. Add Ember/Frost/Volt + the Steam Engine fusion to validate the fusion pipeline end-to-end (data-driven definitions).
5. Playtest on real devices early — thumb occlusion and haptic tuning can't be judged in an editor.
