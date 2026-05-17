---
title: Axes
description: "Information about the Axes skill."
published: true
date: 2024-11-24T01:41:23.115Z
tags: skills, axes
editor: markdown
dateCreated: 2022-07-17T14:29:42.727Z
---

# Axes

The Axes skill enhances combat with all axe-type weapons. Levelling Axes unlocks passive damage bonuses (Axe Mastery), guaranteed critical hits (Critical Strikes), a knockback and bonus-damage proc against unarmoured targets (Greater Impact), armor durability reduction (Armor Impact), an area-of-effect strike (Skull Splitter), and bonus damage scaling with armor rating (Axes Limit Break).

## At a glance

| | |
|---|---|
| **Category** | Combat (melee) |
| **Primary tool** | Axe |
| **Super ability** | Skull Splitter |
| **Parent skill(s)** | None |
| **Child skill(s)** | None |

## XP Gain

XP is earned based on the amount of damage dealt to mobs or players when wielding an axe. XP is proportional to damage dealt; heavier hits grant more XP.

## Sub-Skills

### Axe Mastery

**Ranks:** 4

Axe Mastery adds a flat HP bonus to every axe hit. It is always active once unlocked and does not have a proc chance. The bonus equals `rank × RankDamageMultiplier` (default 1.0), giving +1.0, +2.0, +3.0, and +4.0 HP at ranks 1–4 respectively.

| Rank | Unlock level | Bonus damage (HP) |
|------|-------------|-------------------|
| 1 | 50 | 1.0 |
| 2 | 100 | 2.0 |
| 3 | 150 | 3.0 |
| 4 | 200 | 4.0 |

**Config keys** (`advanced.yml` under `Skills.Axes.AxeMastery`):

| Key | Default | Description |
|-----|---------|-------------|
| `RankDamageMultiplier` | `1.0` | HP bonus added per rank |

---

### Critical Strikes

**Ranks:** 1, Unlocks at level 1

Critical Strikes is a passive proc that multiplies the total damage of an axe hit. The proc chance scales linearly from 0% at level 0 to **37.5%** at level 1000. When it procs, the bonus damage (the portion above the base hit) is scaled by the attack strength modifier.

| Mode | Damage multiplier |
|------|-------------------|
| PvE (vs mobs) | ×2.0 |
| PvP (vs players) | ×1.5 |

**Config keys** (`advanced.yml` under `Skills.Axes.CriticalStrikes`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `37.50` | Maximum proc chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which max chance is reached |
| `PVE_Modifier` | `2.0` | Damage multiplier vs mobs |
| `PVP_Modifier` | `1.5` | Damage multiplier vs players |

---

### Greater Impact

**Ranks:** 1, Unlocks at level 250

Greater Impact is a passive proc that triggers only against targets wearing **no armor**. The proc chance is a flat **25%** regardless of skill level. On proc, it deals bonus damage and launches the target backwards. The bonus damage is scaled by the attack strength modifier at the moment of the hit.

| Attribute | Value |
|-----------|-------|
| Proc chance | 25% (flat) |
| Bonus damage (HP at full charge) | 2.0 |
| Knockback multiplier | 1.5× velocity |

**Config keys** (`advanced.yml` under `Skills.Axes.GreaterImpact`):

| Key | Default | Description |
|-----|---------|-------------|
| `Chance` | `25.0` | Flat proc chance (%), not affected by skill level |
| `BonusDamage` | `2.0` | Extra HP on proc (before attack strength scaling) |
| `KnockbackModifier` | `1.5` | Velocity multiplier applied to target |

---

### Armor Impact

**Ranks:** 20

Armor Impact is a passive proc that triggers only against targets wearing **at least one piece of armor**. On proc, it damages the durability of each armor piece the target is wearing. The proc chance is a flat **25%** per armor piece, checked independently for each piece. The durability damage scales with rank.

Durability damage per proc = `rank × DamagePerRank` (default 6.5 per rank).

| Rank | Unlock level | Durability damage per piece |
|------|-------------|----------------------------|
| 1 | 1 | 6.5 |
| 2 | 100 | 13.0 |
| 3 | 150 | 19.5 |
| 4 | 200 | 26.0 |
| 5 | 250 | 32.5 |
| 6 | 300 | 39.0 |
| 7 | 350 | 45.5 |
| 8 | 400 | 52.0 |
| 9 | 450 | 58.5 |
| 10 | 500 | 65.0 |
| 11 | 550 | 71.5 |
| 12 | 600 | 78.0 |
| 13 | 650 | 84.5 |
| 14 | 700 | 91.0 |
| 15 | 750 | 97.5 |
| 16 | 800 | 104.0 |
| 17 | 850 | 110.5 |
| 18 | 900 | 117.0 |
| 19 | 950 | 123.5 |
| 20 | 1000 | 130.0 |

**Config keys** (`advanced.yml` under `Skills.Axes.ArmorImpact`):

| Key | Default | Description |
|-----|---------|-------------|
| `DamagePerRank` | `6.5` | Durability damage multiplied by rank |
| `Chance` | `25.0` | Flat proc chance (%) per armor piece, not affected by skill level |

---

### Skull Splitter

**Ranks:** 1, Unlocks at level 50

Skull Splitter is an active ability that must be armed by right-clicking with an axe while not looking at a block. When active, the next axe attack deals 50% of the hit's damage (scaled by attack strength) to all enemies within **2.5 blocks** of the primary target.

The maximum number of additional targets hit by the AoE scales with weapon material:

| Weapon material | Max additional targets |
|----------------|----------------------|
| Wood | 1 |
| Stone | 2 |
| Iron | 3 |
| Gold | 1 |
| Diamond | 4 |
| Netherite | 5 |

**Config keys** (`advanced.yml` under `Skills.Axes.SkullSplitter`):

| Key | Default | Description |
|-----|---------|-------------|
| `DamageModifier` | `2.0` | Divisor applied to damage for AoE (damage / 2 = 50%) |

---

### Axes Limit Break

**Ranks:** 10

Axes Limit Break is a passive sub-skill that adds bonus damage to axe hits against targets who have high armor values. The bonus scales with rank and is modified by the quality of the defender's armor. By default it only applies in PvP; enabling `Skills.General.LimitBreak.AllowPVE` in `advanced.yml` also activates it against mobs.

| Rank | Unlock level |
|------|-------------|
| 1 | 100 |
| 2 | 200 |
| 3 | 300 |
| 4 | 400 |
| 5 | 500 |
| 6 | 600 |
| 7 | 700 |
| 8 | 800 |
| 9 | 900 |
| 10 | 1000 |

The raw bonus equals the rank, then modified by the defender's armor quality score:

| Defender armour quality | Damage modifier |
|------------------------|----------------|
| 0 – 4 (e.g. leather) | ×0.25 |
| 5 – 8 (e.g. iron) | ×0.50 |
| 9 – 12 (e.g. chainmail) | ×0.75 |
| > 12 (e.g. diamond/netherite) | ×1.00 |

Against mobs (when PvE is enabled), the full ×1.00 modifier always applies. See the [Limit Break](/skills/limit-break) page for details on armor quality scores by material.

---

## Commands

| Command | Description |
|---------|-------------|
| `/axes` | Display your Axes skill stats and sub-skill information. |
| `/mctop axes` | View the Axes leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Limit Break](skills/limit-break.md): armor-scaling bonus damage shared by every combat skill
- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
