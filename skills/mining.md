---
title: Mining
description: Information about the Mining skill.
published: true
date: 2026-05-11T00:00:00.000Z
tags: mining, skills
editor: markdown
dateCreated: 2022-07-17T14:27:25.815Z
---

# Mining

**Mining** is a [skill](/skills) that rewards breaking stone and ore blocks with a pickaxe. It increases bonus drops from mining and is unique in having two Super Abilities, Super Breaker for mining and Blast Mining for TNT.

## At a glance

| | |
|---|---|
| **Category** | Gathering |
| **Primary tool** | Pickaxe (and TNT for Blast Mining) |
| **Super ability** | Super Breaker · Blast Mining |
| **Parent skill(s)** | None |
| **Child skill(s)** | Smelting (with Repair) |

## Experience Gain

Experience is earned by breaking blocks with a pickaxe. Per-block XP values are configured in `experience.yml` under `Experience_Values.Mining` and can be customised per server. The default values are listed below.

### Ores

| Block | XP |
|-------|---:|
| Ancient Debris | 7777 |
| Deepslate Diamond Ore | 3600 |
| Diamond Ore | 2400 |
| Deepslate Copper Ore | 1900 |
| Deepslate Gold Ore | 1900 |
| Deepslate Emerald Ore | 1700 |
| Copper Ore | 1400 |
| Deepslate Lapis Ore | 1400 |
| Deepslate Iron Ore | 1300 |
| Gold Ore | 1300 |
| Nether Gold Ore | 1300 |
| Emerald Ore | 1000 |
| Iron Ore | 900 |
| Deepslate Redstone Ore | 900 |
| Lapis Lazuli Ore | 800 |
| Deepslate Coal Ore | 700 |
| Redstone Ore | 600 |
| Coal Ore | 400 |
| Nether Quartz Ore | 300 |
| Gilded Blackstone | 200 |

### Stone & terrain

| Block | XP |
|-------|---:|
| Reinforced Deepslate | 500 |
| Smooth Basalt | 300 |
| Obsidian | 150 |
| Blackstone | 55 |
| Basalt | 40 |
| Mud Bricks | 40 |
| Dripstone Block | 35 |
| Deepslate | 30 |
| Magma Block | 30 |
| Mossy Cobblestone | 30 |
| Packed Mud | 30 |
| Sandstone | 30 |
| Terracotta | 30 |
| Andesite | 15 |
| Blue Ice | 15 |
| Cobbled Deepslate | 15 |
| Diorite | 15 |
| End Stone | 15 |
| Glowstone | 15 |
| Granite | 15 |
| Netherrack | 15 |
| Packed Ice | 15 |
| Stone | 15 |
| Tuff | 10 |
| Crimson Nylium | 5 |
| Warped Nylium | 5 |

### Decorative & polished blocks

| Block | XP |
|-------|---:|
| Crying Obsidian | 3000 |
| Purpur Pillar | 250 |
| Purpur Stairs | 250 |
| Purpur Block | 200 |
| Purpur Slab | 150 |
| Red Sandstone | 100 |
| Chain | 100 |
| Prismarine / Prismarine Bricks / Dark Prismarine | 70 |
| Sea Lantern | 70 |
| Nether Bricks (all variants) | 50 |
| Stone Bricks (all variants) | 50 |
| End Bricks | 50 |
| Coloured Terracotta (all 16 colours) | 50 |

### Amethyst

| Block | XP |
|-------|---:|
| Amethyst Block | 500 |
| Budding Amethyst | 400 |
| Amethyst Cluster | 60 |
| Large Amethyst Bud | 30 |
| Medium Amethyst Bud | 20 |
| Small Amethyst Bud | 10 |

### Sculk

| Block | XP |
|-------|---:|
| Sculk Shrieker | 12 |
| Sculk Catalyst | 10 |
| Sculk Sensor | 6 |
| Sculk | 4 |
| Sculk Vein | 3 |

### Coral blocks (broken with a pickaxe)

| Block | XP |
|-------|---:|
| Horn Coral Block | 125 |
| Fire Coral Block | 90 |
| Brain Coral Block | 80 |
| Tube Coral Block | 75 |
| Bubble Coral Block | 70 |

### Other

| Block | XP |
|-------|---:|
| Bone Block | 500 |
| Calcite | 400 |

## Double Drops

**Ranks:** 1

> Unlocks at level **1**.
{.is-info}

A passive chance to receive one extra drop whenever you break a compatible block. The chance scales linearly from **0%** at level 0 to **100%** at level **1000**.

| Level | Double Drop Chance |
|------:|-------------------:|
| 100 | 10% |
| 250 | 25% |
| 500 | 50% |
| 750 | 75% |
| 1000 | 100% |

Double Drops works with Silk Touch by default. It can be disabled for Silk Touch tools:

```yaml
Skills:
  Mining:
    DoubleDrops:
      SilkTouch: false
```

## Mother Lode

**Ranks:** 1

> Unlocks at level **1000**.
{.is-info}

When Double Drops triggers, Mother Lode can fire a **second** bonus drop roll on top of it, effectively tripling yields. Mother Lode only rolls after Double Drops succeeds, so both sub-skills must fire for a triple drop to occur.

The chance scales from **0%** at level 1000 to **50%** at level **10000**.

| Level | Mother Lode Chance |
|------:|-------------------:|
| 1000 | 0% |
| 3250 | 12.5% |
| 5500 | 25% |
| 7750 | 37.5% |
| 10000 | 50% |

## Super Breaker

**Ranks:** 1

> Unlocks at level **50**.
{.is-info}

An active ability. Right-click to ready your pickaxe, then break any compatible block within ~4 seconds to activate Super Breaker. While active, your pickaxe is temporarily enchanted with Efficiency at the level set by `EnchantBuff` (default: **5**), on top of any existing Efficiency, dramatically increasing mining speed. Triple Drops are also enabled, if Double Drops triggers while Super Breaker is active, the drop becomes a triple instead of a double. When the ability ends, the temporary enchant is removed and the ability enters a cooldown.

Duration scales with your Mining level, starting at 3 seconds at level 50 and gaining 1 second every additional 50 levels, up to a default maximum of 1000 seconds.

| Mining Level | Duration |
|-------------:|---------:|
| 50           | 3s       |
| 100          | 4s       |
| 200          | 6s       |
| 500          | 12s      |
| 1000         | 22s      |
| 2000         | 42s      |

| Property | Key | Default | Description |
|----------|-----|---------|-------------|
| Unlock level | `skillranks.yml` → `Mining.SuperBreaker.RetroMode.Rank_1` | `50` | Minimum skill level to unlock this ability |
| Cooldown | `config.yml` → `Abilities.Cooldowns.Super_Breaker` | `240s` | Seconds before the ability can be activated again |
| Max duration | `config.yml` → `Abilities.Max_Seconds.Super_Breaker` | `0` (no cap) | Per-ability duration ceiling in seconds. Only takes effect if lower than the global duration cap; 0 disables this cap entirely |
| Global duration cap | `advanced.yml` → `Skills.General.Ability.Length.RetroMode.CapLevel` | `1000s` | Maximum duration for all super abilities |
| EnchantBuff | `advanced.yml` → `Skills.General.Ability.EnchantBuff` | `5` | Efficiency enchantment level applied to the pickaxe during the ability |

Triple Drops via Super Breaker can be disabled:

```yaml
Skills:
  Mining:
    SuperBreaker:
      AllowTripleDrops: false
```

## Blast Mining

**Ranks:** 8

> Unlocks at level **100**.
{.is-info}

Right-click TNT with a Flint and Steel to remotely detonate it. Each rank improves ore yield, reduces debris drops, reduces self-damage from the explosion, multiplies dropped items, and expands the blast radius.

| Rank | Unlock | Blast Dmg Reduction | Ore Bonus | Debris Reduction | Drop Multiplier | Radius Bonus |
|-----:|-------:|--------------------:|----------:|-----------------:|----------------:|-------------:|
| 1 | 100 | 0% | 35% | 10% | ×1 | +1.0 |
| 2 | 250 | 0% | 40% | 20% | ×1 | +1.0 |
| 3 | 350 | 0% | 45% | 30% | ×1 | +2.0 |
| 4 | 500 | 25% | 50% | 30% | ×1 | +2.0 |
| 5 | 650 | 25% | 55% | 30% | ×2 | +3.0 |
| 6 | 750 | 50% | 60% | 30% | ×2 | +3.0 |
| 7 | 850 | 50% | 65% | 30% | ×3 | +4.0 |
| 8 | 1000 | 100% | 70% | 30% | ×3 | +4.0 |

- **Ore Bonus:** extra chance that ore blocks drop their item rather than the ore block itself.
- **Debris Reduction:** chance that non-ore blocks (stone, gravel, etc.) drop nothing.
- **Drop Multiplier:** all items that do drop are multiplied by this factor.
- At Rank 8, blast self-damage is completely negated.

## Commands

| Command | Description |
|---------|-------------|
| `/mining` | Display your Mining skill stats and sub-skill information. |
| `/mctop mining` | View the Mining leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Smelting](skills/smelting.md): child skill that draws from Mining and Repair
- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
