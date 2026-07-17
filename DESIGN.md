# VIOLET EDGE — design reference

Living roster of hazards and enemies. **✅ implemented · 🔷 planned.** Behaviour notes are the
intended design; implemented rows describe what the code does today.

## Design rules

- **Asteroids are the theme.** Every other hazard exists to change *how you engage the rocks*, never
  to replace them. Enemies stay a fraction of the live asteroid count and thin themselves out — the
  field is always mostly rocks.
- **Each boss weaponizes one *relationship to asteroids*** (a verb): hoard · eat · shoot · prime ·
  pulse · pull · split · reflect · link. The boss is a lens on the rock field, not a separate spectacle.
- **Each powerup is thematically derived from the boss whose defeat drops it** — the reward echoes the
  mechanic you just beat (chain shot ← the Warden *linking* rocks; mass shot ← the red Glutton gaining
  *mass*; drone ← the enemy *ship*). The base Warp weapon is core kit and exempt.
- **Difficult but fair.** Manageable chaos is welcome; only pull back at unavoidable/instant death.
  Leave skill-gated tricks for players to discover rather than hand-holding them.

## Asteroids

| Colour | Status | Behaviour |
| --- | --- | --- |
| **Blue** | ✅ | The standard rock. Sizes L/M/S (radius 88 / 46 / 22); a hit splits it into two of the next size down, the smallest is destroyed. One bullet per break. |
| **Green** | ✅ | Dense — takes multiple hits (HP = size, so a large green needs 3). A normal bullet *chips* it; the chain beam, a mine blast, or a **mass shot** shear it in one. Introduced wave 6 (mixed with blue), waves 7–9 are all green. |
| **Orange** | 🔷 | Explosive. On destruction it detonates, destroying/damaging everything in a radius — other asteroids, mines, enemies (and the player). Detonating another orange in range sets off a **chain reaction**. |
| **Red** | 🔷 | Grows, like the Glutton boss: absorbs nearby asteroids to gain size. A large red that's broken splits into two, and *those* can absorb more and swell back up — an emergent "whack-a-mole" if you don't clear the field around them. |
| **Pulser** | 🔷 | Pulses bright white on a cycle; **invulnerable while lit**. You have to time shots to its dark phase. |

## Enemies

Minor by design — capped as a fraction of the live asteroid count, and they flee/despawn over a
lifetime so the field stays mostly rocks. Three types total is the ceiling; more starts competing
with the asteroids for attention.

| Enemy | Status | Behaviour |
| --- | --- | --- |
| **Yellow mob** | ✅ | Standard enemy ship. Glides in, hovers and strafes around the player, steers clear of rocks/mines, lobs slow (dodgeable) shots, and flees off-screen after a lifetime. Runs in two windows: waves 3–4 and 8–9. |
| **Miner** | 🔷 | Clings to and rides an asteroid as cover, popping out to fire. Kill the rock or catch it exposed. Debuts Act II. |
| **Darter** | 🔷 | Fast interceptor — telegraphs, then charges in a straight line. Pure dodge, no ranged threat. Debuts Act III. |

## Bosses — the 50-level ladder

Every 5th wave. Each weaponizes a different *relationship to asteroids* (see Design rules).

| Wave | Boss | Status | Verb → mechanic | Counterplay |
| --- | --- | --- | --- | --- |
| 5 | **The Warden** | ✅ | *Hoard* — shield of captured rocks on rotating arms; hurls the small ones | Strip the shield, shoot the core through the gaps (bullets hurt the core; chain/warp don't) |
| 10 | **The Glutton** | ✅ | *Eat* — red seeker devours free rocks to grow bigger & tankier | Starve it: clear the field while chipping its (high) HP |
| 15 | **The Slinger** | 🔷 | *Shoot* — large enemy ship lines a big rock between you two and blasts it at you like a cannonball | Keep the lane clear / juke the shot; break its ammo first |
| 20 | **The Detonator** | 🔷 | *Prime* — turns nearby rocks into live bombs; itself armored | Bait the chain — only explosive blasts crack its shell |
| 25 | **The Pulsar** | 🔷 | *Pulse* — invulnerable while lit; shockwaves fling every rock (and you) outward | Hit only on the dark beat; don't get pinned to a wall |
| 30 | **The Singularity** | 🔷 | *Pull* — gravity drags all rocks + you into a crushing orbit | Thrust against the pull; let it crush on its own haul, or feed it an explosive |
| 35 | **The Hive** | 🔷 | *Split* — the boss **is** an asteroid; every hit mitoses, fragments re-fuse if ignored | Burn all pieces down before they merge |
| 40 | **The Prism** | 🔷 | *Reflect* — facets bounce your shots; spawns crystal rocks that also reflect | Catch an open facet, or shoot it *through* a rock |
| 45 | **Gemini** | 🔷 | *Link* — twin ships tethered by a shared rock core; damage transfers between them | Break the core rock to sever them, then focus one |
| 50 | **The Progenitor** | 🔷 | *All* — the first asteroid; cycles the earlier verbs as phases | Apply each phase's counter in turn — a full-run mastery check |

## Pickups (powerups) ↔ boss mapping

Each boss drops a powerup that echoes its own mechanic.

| Boss (drop) | Powerup | Status | Thematic tie |
| --- | --- | --- | --- |
| Warden (W5) | **Chain Shot** | ✅ | beam arcs/*links* between rocks — the Warden links rocks on its arms |
| Glutton (W10) | **Mass Shot** | ✅ | heavier, high-*mass* rounds — the red Glutton gains mass |
| Slinger (W15) | **Drone** | 🔷 | an ally *ship* that seeks & fires for you — mirrors the enemy ship |
| Detonator (W20) | **Warhead rounds** | 🔷 | your shots detonate & chain — echoes the primed bombs |
| Pulsar (W25) | **Nova pulse** | 🔷 | a shockwave that shoves rocks away — echoes its pulse |
| Singularity (W30) | **Magnet** | 🔷 | pulls pickups/small rocks in — echoes its gravity (base Warp stays core kit) |
| Hive (W35) | **Spread shot** | 🔷 | your shot *splits* into several — echoes mitosis |
| Prism (W40) | **Ricochet rounds** | 🔷 | bullets *reflect* off walls/rocks — echoes the facets |
| Gemini (W45) | **Twin cannons** | 🔷 | two linked fire streams — echoes the twins (kept distinct from the drone) |
| Progenitor (W50) | — | — | final boss; no drop (or a combined ultimate) |

> Resolve at implementation: Drone (W15) vs Twin cannons (W45) must feel distinct, and Magnet (W30)
> must not just re-skin the base Warp weapon.

## Progression — 5 acts

Each new asteroid debuts a few waves *before* the boss that weaponizes it: learn the toy, then fight
the thing made of it. (This replaces the current "loop 1–10" scaffold; until the arc is built,
content still repeats 1–10.)

| Act | Waves | New asteroid(s) | New enemy | Bosses |
| --- | --- | --- | --- | --- |
| I — The Field | 1–10 | Blue, Green ✅ | Yellow mob ✅ | Warden (5), Glutton (10) |
| II — Volatile | 11–20 | Orange (explosive) | Miner | Slinger (15), Detonator (20) |
| III — Unstable | 21–30 | Red (growing), Pulser (invuln-lit) | Darter | Pulsar (25), Singularity (30) |
| IV — Deep Belt | 31–40 | **Crystal** (reflects) *or* **Ice** (shard-burst) — TBD | — | Hive (35), Prism (40) |
| V — The Core | 41–50 | **Void** (swallows bullets) *or* **Magnetic** (bends fire) — TBD | — | Gemini (45), Progenitor (50) |

## Life economy (proposed — decision pending)

50 levels on 3 lives is likely impossible, especially a no-powerup **Purist** run. We need earn-able
life recovery that stays skill-gated (not a giveaway). Candidates — cap every source at a shared max
(~5) so lives can't snowball:

- **Score extends (capped)** — *leading.* Classic Asteroids: a free ship at score thresholds (e.g.
  15k, then every 30k). Skill-scaled, on-theme, and works for Purist runs since lives aren't powerups.
- **Boss-clear +1 (capped)** — a life per boss defeated; reliable milestone recovery, pair with a low cap.
- **Rare gold 1UP rock** — a gold asteroid occasionally drifts in; break it for a life. Discovery
  flavor, low reliability; good as spice on top of another source.
- **Perfect-wave meter** — a no-hit wave fills a meter toward a life; rewards clean play, hardest to telegraph.

## Related systems

- **Achievements:** First Blood, Warden Off, Glutton for Punishment, True Blue (100 blue), Green Thumb (100 green), Edgelord (beat the arc), Purist (beat it with no powerups). New bosses each get one, named for the boss.
- **Field population:** the on-screen count targets `POP_BASE + wave` (cap `POP_CAP`), topped up from the edges at `SPAWN_INTERVAL`. Edge spawns are ~80% large; a `BIG_FLOOR` keeps large rocks present even at the cap. Rocks that drift fully off-screen are recycled back in *only if large* — small debris usually despawns for good (mids sometimes), so breaking rocks apart can't silt the arena up with an overwhelming cloud of little ones; the top-up refills with fresh large rocks. The Warden grabs large/mid rocks for its shield and only resorts to a small one when nothing bigger is on-screen.
