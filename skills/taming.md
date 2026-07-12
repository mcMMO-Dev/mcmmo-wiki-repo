---
title: Taming
description: "Information about the Taming skill."
published: true
date: 2026-07-12T00:00:00.000Z
tags: skills, taming
editor: markdown
dateCreated: 2022-07-17T14:29:42.727Z
---

# Taming

The Taming skill enhances animal companions, primarily wolves. It grants passive buffs to wolves that scale with your Taming level, as well as the ability to summon temporary companions and inspect animal stats. Taming has **10 sub-skills:** the most of any mcMMO skill.

## At a glance

| | |
|---|---|
| **Category** | Combat (support) / utility |
| **Primary tool** | Bone (to tame), then summoning items per pet |
| **Super ability** | None |
| **Parent skill(s)** | None |
| **Child skill(s)** | None |

## XP Gain

Taming XP is earned in two ways:

1. **Taming an animal:** a one-time XP reward when the animal becomes yours. The value depends on the species. These values are configured in `experience.yml` under `Experience_Values.Taming.Animal_Taming`.
2. **Combat damage dealt by a wolf you own:** your wolf's hits award you Taming XP proportional to the damage dealt, scaled by the global combat multiplier and species modifier of the target.

### Animal taming XP (per animal tamed)

| Animal | XP |
|--------|---:|
| Nautilus / Zombie Nautilus | 1700 |
| Sniffer | 1500 |
| Camel / Camel Husk | 1300 |
| Llama | 1200 |
| Parrot | 1100 |
| Horse / Donkey / Mule / Skeleton Horse / Zombie Horse | 1000 |
| Fox / Panda | 1000 |
| Frog | 900 |
| Snifflet | 900 |
| Axolotl | 600 |
| Cat / Ocelot | 500 |
| Wolf / Goat | 250 |
| Bee | 100 |

## Sub-Skills

All wolf-based passive sub-skills apply only to wolves you own. They activate automatically when your wolves take or deal damage.

---

### Beast Lore

**Ranks:** 1, Unlocks at level 1

Beast Lore is an active ability that displays detailed information about a tamed animal. Right-click any tameable mob to see its current and maximum HP, its owner, and, for horses, mules, and donkeys, their movement speed and estimated jump height in blocks.

---

### Call of the Wild

**Ranks:** 1, Unlocks at level 1

Call of the Wild allows you to summon a temporary tamed companion by right-clicking while holding specific items. A summoned companion despawns once its summon lifespan expires (default 240 seconds), or sooner if it dies or you log out. Each companion type also has a per-player cap on how many you can have summoned at once.

| Companion | Item held | Quantity consumed | Summon cap |
|-----------|-----------|-------------------|-----------:|
| Wolf | Bones | 10 | 2 |
| Ocelot / Cat | Cod | 10 | 1 |
| Horse | Apples | 10 | 1 |

Summoned horses have a random jump strength between the configured minimum and maximum values (default: 0.7–2.0).

**Config keys** (`advanced.yml` under `Skills.Taming.CallOfTheWild`):

| Key | Default | Description |
|-----|---------|-------------|
| `MinHorseJumpStrength` | `0.7` | Minimum jump strength of a summoned horse |
| `MaxHorseJumpStrength` | `2.0` | Maximum jump strength of a summoned horse |

---

### Environmentally Aware

**Ranks:** 1, Unlocks at level 100

Environmentally Aware protects your wolves from environmental damage, but it behaves differently depending on the source:

- **Fall damage:** while the sub-skill is unlocked, all fall damage to your wolves is cancelled outright. The wolf is not teleported.
- **Fire, lava, hot floor, and contact damage:** the wolf is teleported to your location, but only when the hit is survivable (its damage does not exceed the wolf's current HP). The teleport does not cancel the damage, and lethal hits of these types are not intercepted.

---

### Fast Food Service

**Ranks:** 1, Unlocks at level 200

Fast Food Service gives your wolves a flat **50%** chance to heal HP equal to the damage they deal on each hit. Healing cannot exceed the wolf''s maximum HP.

**Config keys** (`advanced.yml` under `Skills.Taming.FastFoodService`):

| Key | Default | Description |
|-----|---------|-------------|
| `Chance` | `50.0` | Flat chance (%) for healing proc per wolf hit |

---

### Gore

**Ranks:** 1, Unlocks at level 150

Gore gives your wolves a chance to deal **2× damage** and apply a short bleed (Rupture rank 1) on each attack. The proc chance scales linearly from 0% at level 0 to **100%** at level 1000.

**Config keys** (`advanced.yml` under `Skills.Taming.Gore`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `100.0` | Maximum proc chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which max chance is reached |
| `Modifier` | `2.0` | Damage multiplier on proc |

---

### Holy Hound

**Ranks:** 1, Unlocks at level 350

Holy Hound offsets certain damage types with healing for your wolves. When a wolf you own takes **Magic, Poison, or Wither** damage, it is first healed by an amount equal to that damage (capped at its maximum HP), which counteracts the incoming hit. The damage event itself is not cancelled, so the wolf still takes the damage; the pre-heal absorbs it. Because the heal is capped at max HP, a wolf already near full health can end up slightly lower after the exchange.

---

### Pummel

**Ranks:** 1, Unlocks at level 200

Pummel gives your wolves a flat **10%** chance to knock back their target (1.5× velocity) on each hit, similar to the Greater Impact axe proc.

**Config keys** (`advanced.yml` under `Skills.Taming.Pummel`):

| Key | Default | Description |
|-----|---------|-------------|
| `Chance` | `10.0` | Flat knockback proc chance (%) |

---

### Sharpened Claws

**Ranks:** 1, Unlocks at level 750

Sharpened Claws adds a flat **+2.0 HP** bonus to every attack your wolves make.

**Config keys** (`advanced.yml` under `Skills.Taming.SharpenedClaws`):

| Key | Default | Description |
|-----|---------|-------------|
| `Bonus` | `2.0` | Flat HP bonus added to wolf attack damage |

---

### Shock Proof

**Ranks:** 1, Unlocks at level 500

Shock Proof reduces explosion and lightning damage taken by your wolves by a divisor of **6** (i.e., wolves take 1/6 of the raw explosion damage). If the final damage is 0, the event is cancelled.

**Config keys** (`advanced.yml` under `Skills.Taming.ShockProof`):

| Key | Default | Description |
|-----|---------|-------------|
| `Modifier` | `6.0` | Divisor applied to explosion damage |

---

### Thick Fur

**Ranks:** 1, Unlocks at level 250

Thick Fur gives your wolves two passive protections:
- **Physical attacks:** Wolf takes half damage (divisor of 2.0).
- **Fire damage:** The wolf is extinguished (its fire ticks are reset to 0) so it stops taking further burn damage, but the current fire-tick damage still lands; it is not cancelled.

**Config keys** (`advanced.yml` under `Skills.Taming.ThickFur`):

| Key | Default | Description |
|-----|---------|-------------|
| `Modifier` | `2.0` | Divisor applied to physical damage |

---

## Commands

| Command | Description |
|---------|-------------|
| `/taming` | Display your Taming skill stats and sub-skill information. |
| `/mctop taming` | View the Taming leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
- [Configuration](/config)
