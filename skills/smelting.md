---
title: Smelting
description: "Information about the Smelting skill."
published: true
date: 2026-07-12T00:00:00.000Z
tags: smelting, skills
editor: markdown
dateCreated: 2024-11-24T01:59:07.533Z
---

# Smelting

The Smelting skill improves furnace efficiency. Levelling Smelting boosts vanilla XP gained from smelting (Understanding the Art), reduces fuel consumption (Fuel Efficiency), and gives a chance to produce an extra smelted item from each operation (Second Smelt).

> Smelting is a **child skill** of Mining and Repair. Your Smelting level equals the average of your Mining and Repair levels: `Smelting level = floor((Mining + Repair) / 2)`. You cannot level Smelting directly -- improve Mining and Repair to increase it.
{.is-info}

## At a glance

| | |
|---|---|
| **Category** | Utility / crafting (child skill) |
| **Primary tool** | Furnace |
| **Super ability** | None |
| **Parent skill(s)** | Mining + Repair |
| **Child skill(s)** | None |

## XP Gain

When a furnace completes a smelt operation, mcMMO XP is awarded and split equally between **Mining** and **Repair**. The amount per smelt depends on the source item being smelted:

| Source item | mcMMO XP |
|-------------|----------|
| Ancient Debris | 200 |
| Deepslate Diamond Ore | 140 |
| Deepslate Copper Ore | 100 |
| Emerald Ore | 100 |
| Deepslate Emerald Ore | 110 |
| Copper Nugget | 85 |
| Diamond Ore | 75 |
| Copper Ore / Raw Copper | 75 |
| Deepslate Lapis Lazuli Ore | 60 |
| Deepslate Gold Ore | 50 |
| Lapis Lazuli Ore / Lapis Ore | 40 |
| Deepslate Iron Ore | 40 |
| Gold Ore / Raw Gold | 35 |
| Nether Gold Ore | 35 |
| Deepslate Redstone Ore | 30 |
| Iron Ore / Raw Iron | 25 |
| Nether Quartz Ore | 25 |
| Deepslate Coal Ore | 20 |
| Redstone Ore | 15 |
| Coal Ore | 10 |
| Cobbled Deepslate | 5 |

XP amounts are configurable in `experience.yml` under `Smelting`.

## Sub-Skills

### Fuel Efficiency

**Ranks:** 3 -- Unlocks at level 100

Fuel Efficiency increases the burn time of all furnace fuel. When a new piece of fuel is added to a furnace, the burn duration is multiplied by the rank modifier.

| Rank | Unlock level | Burn time multiplier |
|------|-------------|----------------------|
| 1 | 100 | 2x |
| 2 | 500 | 3x |
| 3 | 750 | 4x |

The multiplied burn time is capped at 32,767 ticks (vanilla short max) to prevent overflow.

---

### Second Smelt

**Ranks:** 0 (passive, no rank unlock) -- Active from level 1

Second Smelt gives a passive chance to produce one extra copy of the smelted item from each furnace operation. It only activates if the result slot has room for at least two more items (it will not create an overfull stack).

The proc chance scales linearly from 0% at level 0 to **50%** at level 1000.

**Config keys** (`advanced.yml` under `Skills.Smelting.SecondSmelt`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `50.0` | Maximum proc chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which maximum chance is reached |

> Second Smelt can be disabled per material in `config.yml` under `Bonus_Drops.Smelting`.
{.is-info}

---

### Understanding the Art

**Ranks:** 8 -- Unlocks at level 100

Understanding the Art multiplies the vanilla Minecraft XP dropped when a furnace completes a smelt. Higher ranks provide greater multipliers.

| Rank | Unlock level | Vanilla XP multiplier |
|------|-------------|----------------------|
| 1 | 100 | 1x |
| 2 | 250 | 2x |
| 3 | 350 | 3x |
| 4 | 500 | 3x |
| 5 | 650 | 4x |
| 6 | 750 | 4x |
| 7 | 850 | 5x |
| 8 | 1000 | 5x |

**Config keys** (`advanced.yml` under `Skills.Smelting.VanillaXPMultiplier`):

| Key | Default |
|-----|---------|
| `Rank_1` | `1` |
| `Rank_2` | `2` |
| `Rank_3` | `3` |
| `Rank_4` | `3` |
| `Rank_5` | `4` |
| `Rank_6` | `4` |
| `Rank_7` | `5` |
| `Rank_8` | `5` |

---

## Commands

| Command | Description |
|---------|-------------|
| `/smelting` | Display your Smelting skill stats and sub-skill information. |
| `/mctop smelting` | View the Smelting leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Mining](/skills/mining): parent skill
- [Repair](/skills/repair): parent skill
- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
