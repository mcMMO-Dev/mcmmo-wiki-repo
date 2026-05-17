---
title: Swords
description: "Information about the Swords skill."
published: true
date: 2024-11-24T01:42:04.578Z
tags: skills, swords
editor: markdown
dateCreated: 2022-07-17T14:29:42.727Z
---

# Swords

The Swords skill enhances combat with all sword-type weapons. Levelling Swords unlocks passive damage bonuses (Stab), a bleeding damage-over-time effect (Rupture), an area-of-effect strike (Serrated Strikes), a damage reflection effect (Counter Attack), and bonus damage against heavily armoured targets (Swords Limit Break).

## XP Gain

XP is earned based on the amount of damage dealt to mobs or players when wielding a sword. XP is proportional to damage dealt; heavier hits grant more XP.

## Sub-Skills

### Stab

**Ranks:** 2

Stab adds a flat HP bonus to every sword hit. It is always active once unlocked and does not have a proc chance.

| Rank | Unlock level | Bonus damage (HP) |
|------|-------------|-------------------|
| 1 | 750 | 2.5 |
| 2 | 1000 | 4.0 |

**Formula:** `bonus = Base_Damage + (rank x Per_Rank_Multiplier)` = `1.0 + (rank x 1.5)`

**Config keys** (`advanced.yml` under `Skills.Swords.Stab`):

| Key | Default | Description |
|-----|---------|-------------|
| `Base_Damage` | `1.0` | Base damage added before rank scaling |
| `Per_Rank_Multiplier` | `1.5` | Additional HP added per rank |

---

### Rupture

**Ranks:** 4 -- Unlocks at level 1

Rupture is a passive proc that applies a bleeding damage-over-time effect to the target on each sword hit. Each hit independently rolls against the proc chance. Hitting the target again while Rupture is active refreshes its duration. Blocking prevents Rupture from being applied to player targets.

Rupture damage is **pure** -- it ignores armor, absorption hearts, and other damage reduction effects. Rupture expires after 5 seconds if not refreshed.

Proc chance is multiplied by the attack strength modifier (`procChance x attackStrength`), so charging a sword swing increases the probability.

| Rank | Unlock level | Proc chance per hit | Tick damage vs players (HP) | Tick damage vs mobs (HP) |
|------|-------------|--------------------|-----------------------------|--------------------------|
| 1 | 1 | 15% | 0.1 | 0.5 |
| 2 | 150 | 33% | 0.15 | 0.75 |
| 3 | 750 | 40% | 0.2 | 0.9 |
| 4 | 900 | 66% | 0.3 | 1.0 |

Tick damage is applied twice per second.

**Config keys** (`advanced.yml` under `Skills.Swords.Rupture.Rupture_Mechanics`):

| Key | Default | Description |
|-----|---------|-------------|
| `Chance_To_Apply_On_Hit.Rank_N` | (see table) | Proc chance (%) per rank |
| `Duration_In_Seconds.Against_Players` | `5` | Duration of the bleed effect against players |
| `Duration_In_Seconds.Against_Mobs` | `5` | Duration of the bleed effect against mobs |
| `Tick_Interval_Damage.Against_Players.Rank_N` | (see table) | Pure tick damage per rank |
| `Tick_Interval_Damage.Against_Mobs.Rank_N` | (see table) | Pure tick damage per rank |

---

### Serrated Strikes

**Ranks:** 1 -- Unlocks at level 50

Serrated Strikes is an active ability that must be armed by right-clicking with a sword while not looking at a block. When active, the next sword attack deals 25% of the hit's damage to all enemies within **2.5 blocks** of the primary target and also applies Rupture to each one.

The maximum number of additional targets hit by the AoE scales with weapon material:

| Weapon material | Max additional targets |
|----------------|----------------------|
| Wood | 1 |
| Stone | 2 |
| Iron | 3 |
| Gold | 1 |
| Diamond | 4 |
| Netherite | 5 |

**Config keys** (`advanced.yml` under `Skills.Swords.SerratedStrikes`):

| Key | Default | Description |
|-----|---------|-------------|
| `DamageModifier` | `4.0` | Divisor applied to damage for AoE (damage / 4 = 25%) |

---

### Counter Attack

**Ranks:** 1 -- Unlocks at level 200

Counter Attack is a passive proc that triggers when you take damage from a mob or player while holding a sword. On proc, **50%** of the incoming damage is dealt back to the attacker (ignoring their armor). The counter-damage is subject to event cancellation from other plugins.

The proc chance scales linearly from 0% at level 0 to **30%** at level 1000.

**Config keys** (`advanced.yml` under `Skills.Swords.CounterAttack`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `30.0` | Maximum proc chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which max chance is reached |
| `DamageModifier` | `2.0` | Divisor applied to incoming damage (damage / 2 = 50% reflected) |

---

### Swords Limit Break

**Ranks:** 10

Swords Limit Break is a passive sub-skill that adds bonus damage against targets wearing high-quality armor. The raw bonus equals the player's current rank. It is then modified by the target's total armor quality score. By default it only applies in PvP; enabling `Skills.General.LimitBreak.AllowPVE: true` in `advanced.yml` also activates it against mobs.

> Limit Break damage is also multiplied by your attack strength at the moment of the hit.
{.is-info}

| Rank | Unlock level | Raw bonus damage (HP) |
|------|-------------|----------------------|
| 1 | 100 | 1 |
| 2 | 200 | 2 |
| 3 | 300 | 3 |
| 4 | 400 | 4 |
| 5 | 500 | 5 |
| 6 | 600 | 6 |
| 7 | 700 | 7 |
| 8 | 800 | 8 |
| 9 | 900 | 9 |
| 10 | 1000 | 10 |

**Armor quality modifier:**

| Total armor quality score | Damage modifier |
|--------------------------|-----------------|
| 0 -- 4 | x0.25 |
| 5 -- 8 | x0.50 |
| 9 -- 12 | x0.75 |
| 13+ | x1.00 |

**Armor quality score per piece:**

| Armor material | Score per piece |
|---------------|-----------------|
| Leather / Copper | 1 |
| Iron | 2 |
| Gold / Chainmail | 3 |
| Diamond | 6 |
| Netherite | 12 |

See [Limit Break](/skills/limit-break) for full details on the damage formula and armor quality scoring.

---

## Commands

| Command | Description |
|---------|-------------|
| `/swords` | Display your Swords skill stats and sub-skill information. |
| `/mctop swords` | View the Swords leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |
