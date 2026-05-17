---
title: Alchemy
description: "Information about the Alchemy skill."
published: true
date: 2024-11-24T01:41:12.847Z
tags: alchemy, skills
editor: markdown
dateCreated: 2022-07-16T21:46:19.551Z
---

# Alchemy

The Alchemy skill governs potion brewing. Levelling Alchemy speeds up your brewing process (Catalysis) and unlocks access to additional brewing ingredients that produce potions unavailable in vanilla Minecraft (Concoctions). XP is earned by successfully completing potion brews.

## At a glance

| | |
|---|---|
| **Category** | Utility / crafting |
| **Primary tool** | Brewing Stand |
| **Super ability** | None |
| **Parent skill(s)** | None |
| **Child skill(s)** | None |

> **Compared to vanilla:** vanilla brewing supports a fixed set of recipes and takes a constant time per batch. Alchemy unlocks Concoctions (additional ingredients producing recipes that don't exist in vanilla) and Catalysis (reduced brewing time per rank).
{.is-info}

## XP Gain

XP is awarded each time a brewing operation completes. The amount depends on which stage (how many ingredients have been added to the potion):

| Stage | Description | XP |
|-------|------------|-----|
| Stage 1 | Base potion | 666 |
| Stage 2 | Base potion + 1 ingredient | 1111 |
| Stage 3 | Base potion + 1 ingredient + 1 amplifier | 1750 |
| Stage 4 | Base potion + 1 ingredient + 2 amplifiers | 2250 |
| Stage 5 | Base potion + 1 ingredient with swapped amplifiers | 0 |

XP is multiplied by the number of potions brewed in the batch (up to 3). Values are configurable in `experience.yml` under `Alchemy.Potion_Brewing`.

## Sub-Skills

### Catalysis

**Ranks:** 1, Unlocks at level 0

Catalysis passively increases the speed of all brewing operations. The speed multiplier scales linearly from the minimum (1.0×) at level 0 to the maximum (4.0×) at level 1000.

| Skill level | Brew speed |
|-------------|-----------|
| 0           | 1.0×      |
| 250         | 1.75×     |
| 500         | 2.5×      |
| 750         | 3.25×     |
| 1000+       | 4.0×      |

**Formula:** `speed = min(MaxSpeed, MinSpeed + (MaxSpeed − MinSpeed) × skillLevel / MaxBonusLevel)`

**Config keys** (`advanced.yml` under `Skills.Alchemy.Catalysis`):

| Key | Default | Description |
|-----|---------|-------------|
| `MinSpeed` | `1.0` | Brew speed multiplier before any bonus |
| `MaxSpeed` | `4.0` | Maximum brew speed multiplier |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which MaxSpeed is reached |

> Players with the Lucky perk receive an additional 4/3× multiplier on top of their Catalysis speed.
{.is-info}

> Brewing speed is applied inside mcMMO's own brew timer. When mcMMO takes ownership of a brewing stand (by placing an ingredient), it replaces vanilla's 400-tick countdown with its own task that counts down at `brewSpeed` ticks per server tick. The brewing stand therefore completes in roughly `400 / brewSpeed` ticks. At 4.0× speed that is 100 ticks (5 seconds) instead of the vanilla 20 seconds.
{.is-info}

---

### Concoctions

**Ranks:** 8

Concoctions unlocks additional brewing ingredients that can be used in the brewing stand to create special potions not craftable in vanilla Minecraft. Each rank unlocks a new set of ingredients; your current tier is the highest tier you have access to, and includes all ingredients from lower tiers.

All potion recipes and effects are configurable in `potions.yml`. The default ingredient-to-potion mappings are shown below.

| Rank | Unlock level | Ingredients unlocked | Default potion produced |
|------|-------------|----------------------|------------------------|
| 1 | 0 | Blaze Powder, Breeze Rod, Cobweb, Dragon's Breath, Fermented Spider Eye, Ghast Tear, Glistering Melon Slice, Glowstone Dust, Golden Carrot, Gunpowder, Lily Pad, Magma Cream, Nether Wart, Pufferfish, Redstone, Slime Block, Spider Eye, Stone, Sugar, Turtle Helmet | Vanilla brewing ingredients |
| 2 | 100 | Carrot, Phantom Membrane, Slimeball | Haste / Slow Falling / Dullness |
| 3 | 200 | Quartz, Rabbit's Foot | Absorption / Leaping |
| 4 | 350 | Apple, Rotten Flesh | Health Boost / Hunger |
| 5 | 500 | Brown Mushroom, Ink Sac | Nausea / Blindness |
| 6 | 750 | Fern | Saturation |
| 7 | 900 | Poisonous Potato | Decay |
| 8 | 1000 | Golden Apple | Resistance |

> Concoctions ingredients and their resulting potions are fully configurable in `potions.yml`. Servers may add, remove, or change any Concoctions recipe.
{.is-warning}

---

## Commands

| Command | Description |
|---------|-------------|
| `/alchemy` | Display your Alchemy skill stats and sub-skill information. |
| `/mctop alchemy` | View the Alchemy leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
- [Configuration](/config)
