---
title: Fishing
description: "Information about the Fishing skill."
published: true
date: 2024-11-24T01:41:45.231Z
tags: skills, fishing
editor: markdown
dateCreated: 2022-07-17T14:29:42.727Z
---

# Fishing

The Fishing skill enhances all fishing activities. Levelling Fishing unlocks faster bite times (Master Angler), ice-hole auto-creation (Ice Fishing), rare treasure drops from catches (Treasure Hunter), enchanted book drops (Magic Hunter), improved food healing from fish (Fisherman's Diet), and the ability to shake mobs to force item drops (Shake).

Fishing is also a **parent skill** of Salvage. Your Fishing level contributes to your Salvage level as: `floor((Repair + Fishing) / 2)`.

## XP Gain

XP is earned each time a fish or treasure item is successfully caught. Catching treasure grants the base fish XP plus a bonus based on the treasure rarity. XP values are configured in `experience.yml`.

## Loot System

Vanilla fishing loot and mcMMO Treasure Hunter loot are independent. When you catch something, vanilla first determines whether you get a fish, junk, or treasure. Then mcMMO makes a separate Treasure Hunter roll. It is possible to receive both a vanilla item and an mcMMO treasure from a single cast.

---

## Sub-Skills

### Fisherman's Diet

**Ranks:** 5

Fisherman's Diet increases the amount of hunger restored when eating fish. Each rank adds **+1 hunger point** restored on top of the food's base value. This sub-skill only affects the hunger bar; it does not change saturation.

| Rank | Unlock level | Bonus hunger restored |
|------|-------------|----------------------|
| 1 | 200 | +1 |
| 2 | 400 | +2 |
| 3 | 600 | +3 |
| 4 | 800 | +4 |
| 5 | 1000 | +5 |

---

### Ice Fishing

**Ranks:** 1 -- Unlocks at level 50

Ice Fishing automatically breaks a 3x3 area of ice blocks directly beneath your fishing bobber when it lands, creating an open water hole. This allows fishing in frozen biomes without needing to manually clear ice. The bobber is then automatically recast in the new water.

---

### Magic Hunter

**Ranks:** 1 -- Unlocks at level 200

Magic Hunter enables enchanted books to appear in the Treasure Hunter loot pool. It requires Treasure Hunter to be unlocked (rank 1 at level 1). Enchanted books are drawn from the `treasures.yml` loot tables and can have random enchantments.

---

### Master Angler

**Ranks:** 8

Master Angler reduces the minimum and maximum wait time for a bite. Each rank reduces both the minimum and maximum tick wait by a configurable amount per rank (default: 10 ticks per rank for both min and max). Being in a **boat** grants an additional flat reduction on top of the rank-based reduction.

Vanilla Lure enchantment is properly accounted for -- at Lure levels above 3, mcMMO applies the bonus manually to avoid a Minecraft engine bug.

| Rank | Unlock level |
|------|-------------|
| 1 | 1 |
| 2 | 200 |
| 3 | 300 |
| 4 | 400 |
| 5 | 600 |
| 6 | 700 |
| 7 | 800 |
| 8 | 900 |

**Config keys** (`advanced.yml` under `Skills.Fishing.MasterAngler`):

| Key | Default | Description |
|-----|---------|-------------|
| `Tick_Reduction_Per_Rank.Min_Wait` | `10` | Ticks of min-wait reduction per rank |
| `Tick_Reduction_Per_Rank.Max_Wait` | `10` | Ticks of max-wait reduction per rank |
| `Boat_Tick_Reduction.Min_Wait` | `10` | Additional ticks of min-wait reduction when in a boat |
| `Boat_Tick_Reduction.Max_Wait` | `30` | Additional ticks of max-wait reduction when in a boat |
| `Tick_Reduction_Caps.Min_Wait` | `40` | Minimum allowed min-wait tick floor |
| `Tick_Reduction_Caps.Max_Wait` | `100` | Minimum allowed max-wait tick floor |

---

### Treasure Hunter

**Ranks:** 8

Treasure Hunter gives a chance to catch bonus treasure items instead of (or in addition to) regular fish. The treasure pool and drop chances are defined in `treasures.yml`. Higher ranks unlock rarer treasures and increase drop chances.

| Rank | Unlock level |
|------|-------------|
| 1 | 1 |
| 2 | 250 |
| 3 | 350 |
| 4 | 500 |
| 5 | 650 |
| 6 | 750 |
| 7 | 850 |
| 8 | 1000 |

---

### Shake

**Ranks:** 8 -- Unlocks at level 150

Shake allows you to cast your fishing line at a mob that is in water and force it to drop its held item (the same drops as using the Looting enchantment on that mob type). The mob is not harmed. The proc chance per rank is a fixed value from the config.

| Rank | Unlock level | Proc chance |
|------|-------------|-------------|
| 1 | 150 | 15% |
| 2 | 200 | 20% |
| 3 | 250 | 25% |
| 4 | 300 | 35% |
| 5 | 400 | 45% |
| 6 | 500 | 55% |
| 7 | 600 | 65% |
| 8 | 700 | 75% |

**Config keys** (`advanced.yml` under `Skills.Fishing.ShakeChance`):

| Key | Default | Description |
|-----|---------|-------------|
| `Rank_N` | (see table) | Proc chance per rank |

**Vanilla XP multiplier** (`advanced.yml` under `Skills.Fishing.VanillaXPMultiplier`):

Each Shake rank also multiplies vanilla fishing XP orb drops:

| Rank | Vanilla XP multiplier |
|------|-----------------------|
| 1 | x1 |
| 2 | x2 |
| 3 | x3 |
| 4 | x3 |
| 5 | x4 |
| 6 | x4 |
| 7 | x5 |
| 8 | x5 |

---

## Commands

| Command | Description |
|---------|-------------|
| `/fishing` | Display your Fishing skill stats and sub-skill information. |
| `/mctop fishing` | View the Fishing leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |
