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

**Mining** is a [skill](/skills) that rewards breaking stone and ore blocks with a pickaxe. It increases bonus drops from mining and is unique in having two Super Abilities — Super Breaker for mining and Blast Mining for TNT.

## Experience Gain

Experience is earned by breaking blocks with a pickaxe. The full list is configurable per server, but by default it covers all ore blocks (including Deepslate variants), stone-type blocks, and various Nether blocks.

| Category | Examples |
|----------|---------|
| Overworld ores | Coal, Iron, Gold, Diamond, Emerald, Redstone, Lapis, Copper ore |
| Deepslate ores | Deepslate variants of all overworld ores |
| Stone variants | Stone, Cobblestone, Deepslate, Cobbled Deepslate, Andesite, Diorite, Granite, Sandstone |
| Nether | Netherrack, Ancient Debris, Nether Gold Ore, Nether Quartz Ore, Basalt, Blackstone, Nether Bricks |
| End | End Stone |
| Other | Obsidian, Glowstone, Amethyst clusters and buds, Tuff, Calcite |

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

When Double Drops triggers, Mother Lode can fire a **second** bonus drop roll on top of it — effectively tripling yields. Mother Lode only rolls after Double Drops succeeds, so both sub-skills must fire for a triple drop to occur.

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

An active ability. Right-click to ready your pickaxe, then break any compatible block within ~4 seconds to activate Super Breaker. While active, a temporary Efficiency enchant buff is applied to your pickaxe, dramatically increasing mining speed. Triple Drops are also enabled — if Double Drops triggers while Super Breaker is active, the drop becomes a triple instead of a double. Duration scales with your Mining level.

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

- **Ore Bonus** — extra chance that ore blocks drop their item rather than the ore block itself.
- **Debris Reduction** — chance that non-ore blocks (stone, gravel, etc.) drop nothing.
- **Drop Multiplier** — all items that do drop are multiplied by this factor.
- At Rank 8, blast self-damage is completely negated.
