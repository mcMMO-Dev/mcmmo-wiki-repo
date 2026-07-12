---
title: Mining
description: Information about the Mining skill.
published: true
date: 2026-07-12T00:00:00.000Z
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

### Cinnabar and sulfur

These block families award Mining XP on servers where they are present:

| Block | XP |
|-------|---:|
| Cinnabar (all variants) | 40 |
| Sulfur (all variants) | 40 |
| Potent Sulfur | 60 |
| Sulfur Spike | 30 |

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

Mother Lode is rolled **first and independently** whenever you break a compatible block. If the Mother Lode roll succeeds, the block yields a **triple** drop. If it fails, mcMMO falls back to the normal Double Drops roll, which can still produce a double drop. Only the Mother Lode roll needs to succeed for a triple drop, so Double Drops does not have to fire first.

The chance scales linearly with your Mining level (level ÷ 10000 × 50%), with no unlock floor. Mother Lode unlocks at level **1000**, where the chance is already **5%**, and reaches **50%** at level **10000**.

| Level | Mother Lode Chance |
|------:|-------------------:|
| 1000 | 5% |
| 3250 | 16.25% |
| 5500 | 27.5% |
| 7750 | 38.75% |
| 10000 | 50% |

## Super Breaker

**Ranks:** 1

> Unlocks at level **50**.
{.is-info}

An active ability. Right-click to ready your pickaxe, then break any compatible block within ~4 seconds to activate Super Breaker. While active, a temporary Efficiency enchant buff is applied to your pickaxe, dramatically increasing mining speed. Triple Drops are also enabled, if Double Drops triggers while Super Breaker is active, the drop becomes a triple instead of a double. Duration scales with your Mining level.

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

Crouch and right-click while looking at TNT, holding a pickaxe or a Flint and Steel, to remotely detonate it from up to **100 blocks** away (configurable with `Skills.Mining.BlastMining.RemoteDetonationDistance` in [`advanced.yml`](/config/advanced)). Each rank improves ore yield, reduces self-damage from the explosion, and expands the blast radius. Higher ranks can also produce bonus copies of ore drops.

| Rank | Unlock | Blast Dmg Reduction | Ore Bonus | Radius Bonus |
|-----:|-------:|--------------------:|----------:|-------------:|
| 1 | 100 | 0% | 35% | +1.0 |
| 2 | 250 | 0% | 40% | +1.0 |
| 3 | 350 | 0% | 45% | +2.0 |
| 4 | 500 | 25% | 50% | +2.0 |
| 5 | 650 | 25% | 55% | +3.0 |
| 6 | 750 | 50% | 60% | +3.0 |
| 7 | 850 | 50% | 65% | +4.0 |
| 8 | 1000 | 100% | 70% | +4.0 |

When you detonate TNT, mcMMO cancels the vanilla explosion drops and handles every drop itself:

- **Mining XP:** every destroyed ore always grants Mining XP, whether or not it produces a drop.
- **Ore drops:** each eligible ore's drop chance equals the explosion's yield multiplied by `1 + Ore Bonus`, capped at 300%. Every full 100% is one guaranteed drop and any leftover fraction is the chance of one more drop. Modern servers report a 100% yield for a standard TNT blast, so every eligible ore drops at least once, with a further 35% chance of a second set at rank 1, rising to 70% at rank 8. Drops are rolled with the pickaxe in your hand, so Fortune and Silk Touch apply.
- **Bonus ore drops:** when an ore drop succeeds and `Bonus_Drops.Enabled` is `true` (the default) in [`advanced.yml`](/config/advanced) under `Skills.Mining.BlastMining`, there is a further flat 50% chance to spawn extra copies of that drop. The number of extra copies is fixed by rank: none at ranks 1-2, one extra set at ranks 3-6, and two extra sets at ranks 7-8.
- **Non-ore blocks:** every non-ore block caught in the blast has a flat 10% chance to drop itself, at every rank.
- **Never dropped:** spawners, infested blocks, and budding amethyst never drop, and player-placed blocks are ignored entirely.
- **Self-damage:** the Blast Dmg Reduction column reduces the explosion damage you take; at rank 8 it is completely negated.

## Bigger Bombs

**Ranks:** 1

> Unlocks at level **100**.
{.is-info}

Increases the blast radius of your Blast Mining explosions. The bonus radius grows with your Blast Mining rank; see the Radius Bonus column in the Blast Mining table.

## Demolitions Expertise

**Ranks:** 1

> Unlocks at level **100**.
{.is-info}

Reduces the damage you take from your own Blast Mining explosions. The reduction grows with your Blast Mining rank; see the Blast Dmg Reduction column in the Blast Mining table.

## Commands

| Command | Description |
|---------|-------------|
| `/mining` | Display your Mining skill stats and sub-skill information. |
| `/mctop mining` | View the Mining leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Smelting](/skills/smelting): child skill that draws from Mining and Repair
- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
