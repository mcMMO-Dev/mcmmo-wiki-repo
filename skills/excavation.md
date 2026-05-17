---
title: Excavation
description: "Information about the Excavation skill."
published: true
date: 2024-11-24T01:43:42.890Z
tags: excavation, skills
editor: markdown
dateCreated: 2022-07-17T01:36:33.657Z
---

# Excavation

The Excavation skill governs digging with shovels. XP is earned by breaking compatible blocks with a shovel. Levelling Excavation unlocks the Archaeology passive (treasure drops from soil and sediment blocks) and the Giga Drill Breaker active ability.

## XP Gain

XP is granted each time you break a compatible block while holding a shovel. The amount depends on the block type:

| Block | XP |
|-------|----|
| Muddy Mangrove Roots | 90 |
| Mud | 80 |
| Rooted Dirt | 60 |
| Clay | 40 |
| Coarse Dirt | 40 |
| Dirt | 40 |
| Grass Block | 40 |
| Gravel | 40 |
| Mycelium | 40 |
| Podzol | 40 |
| Red Sand | 40 |
| Sand | 40 |
| Snow Block | 40 |
| Soul Sand | 40 |
| Soul Soil | 40 |
| Snow (layer) | 20 |

XP values are configurable in `experience.yml` under the `Excavation` block.

## Sub-Skills

### Archaeology

**Ranks:** 8

Archaeology is a passive sub-skill that allows treasures to drop from compatible Excavation blocks. Each treasure has its own minimum skill level requirement; only treasures at or below your current skill level are eligible to drop. Higher skill levels unlock a wider pool of treasures.

Each treasure also has an independent drop chance (configurable in `treasures.yml`). When a treasure successfully drops, there is additionally a `rank × 2 %` chance that vanilla XP orbs worth `rank` points are spawned alongside it.

> Treasure drops are entirely configurable via `treasures.yml`. The min-level values in the table below are raw `treasures.yml` defaults and are not automatically scaled by Retro/Standard mode. Servers running Retro mode may wish to scale treasure min levels accordingly in `treasures.yml`.
{.is-warning}

> `treasures.yml` is not automatically updated when mcMMO upgrades. If you have an older `treasures.yml`, new treasures introduced in later releases will not appear until you regenerate or manually update the file.
{.is-info}

**Archaeology rank unlock levels:**

| Rank | Unlock level |
|------|-------------|
| 1    | 1           |
| 2    | 250         |
| 3    | 350         |
| 4    | 500         |
| 5    | 650         |
| 6    | 750         |
| 7    | 850         |
| 8    | 1000        |

**Default treasure table:**

| Item | Amt | Drop chance | Min level (default) | Treasure XP | Source blocks |
|------|-----|-------------|-----------|-------------|---------------|
| Stick | 2 | 2.00 % | 1 | 50 | Mud, Muddy Mangrove Roots |
| Glowstone Dust | 1 | 5.00 % | 5 | 80 | Dirt, Coarse Dirt, Podzol, Grass Block, Sand, Red Sand, Mycelium |
| Feather | 3 | 1.00 % | 5 | 50 | Mud |
| Spyglass | 1 | 0.10 % | 7 | 500 | Mud, Dirt |
| Gunpowder | 1 | 10.00 % | 10 | 30 | Gravel |
| Potato | 1 | 3.00 % | 10 | 50 | Dirt, Mud |
| Slime Ball | 1 | 5.00 % | 15 | 100 | Clay |
| Bone | 1 | 10.00 % | 20 | 30 | Gravel, Mud |
| Apple | 1 | 0.10 % | 25 | 100 | Grass Block, Mycelium |
| Egg | 1 | 1.00 % | 25 | 100 | Grass Block |
| String | 1 | 5.00 % | 25 | 200 | Clay |
| Music Disc 13 | 1 | 0.05 % | 25 | 3000 | Dirt, Coarse Dirt, Podzol, Grass Block, Sand, Red Sand, Gravel, Clay, Mycelium, Soul Sand, Soul Soil |
| Music Disc Cat | 1 | 0.05 % | 25 | 3000 | Same as Music Disc 13 |
| Name Tag | 1 | 0.05 % | 25 | 3000 | Dirt, Coarse Dirt, Podzol, Grass Block, Sand, Red Sand, Gravel, Clay, Mycelium, Soul Sand, Soul Soil |
| Cocoa Beans | 1 | 1.33 % | 35 | 100 | Dirt, Coarse Dirt, Podzol, Grass Block, Mycelium, Mud |
| Diamond | 1 | 0.13 % | 35 | 1000 | Dirt, Coarse Dirt, Podzol, Grass Block, Sand, Red Sand, Gravel, Clay, Mycelium, Soul Sand, Soul Soil, Mud |
| Trident | 1 | 0.02 % | 40 | 100 | Mud, Clay, Muddy Mangrove Roots |
| Red Mushroom | 1 | 0.50 % | 50 | 80 | Dirt, Coarse Dirt, Podzol, Grass Block, Mycelium, Mud |
| Brown Mushroom | 1 | 0.50 % | 50 | 80 | Dirt, Coarse Dirt, Podzol, Grass Block, Mycelium, Mud |
| Bucket | 1 | 0.10 % | 50 | 100 | Clay |
| Clock | 1 | 0.10 % | 50 | 100 | Clay |
| Soul Sand (item) | 1 | 0.50 % | 65 | 80 | Sand, Red Sand |
| Cake | 1 | 0.05 % | 75 | 3000 | Dirt, Coarse Dirt, Podzol, Grass Block, Sand, Red Sand, Gravel, Clay, Mycelium, Soul Sand, Soul Soil |
| Cobweb | 1 | 5.00 % | 75 | 150 | Clay |
| Quartz | 1 | 0.50 % | 85 | 100 | Dirt, Coarse Dirt, Podzol, Grass Block, Sand, Red Sand, Gravel, Mycelium, Soul Sand, Soul Soil |
| Netherrack | 1 | 0.50 % | 85 | 30 | Gravel |
| Heart of the Sea | 1 | 0.01 % | 90 | 9999 | Mud |

---

### Giga Drill Breaker

**Ranks:** 1 — Unlocks at level 50

Giga Drill Breaker is an active ability that dramatically boosts your digging speed and treasure finds. To activate it, right-click with a shovel while holding it to enter the "ready" state, then break any compatible Excavation block.

**While active:**
- Your shovel is temporarily enchanted with **Efficiency +5** (on top of any existing Efficiency), enabling near-instant block breaking for compatible blocks.
- Treasure rolls are **tripled** for the activated block — three independent rolls are made instead of one.
- XP from that block is also **tripled** (three separate XP gains apply).

**Duration** formula: `2 + floor(min(skillLevel, 1000) / 50)` seconds. A player at level 50 gets 3 seconds; the maximum at level 1000 is 22 seconds.

| Skill level | Duration |
|-------------|---------|
| 50          | 3 s     |
| 250         | 7 s     |
| 500         | 12 s    |
| 750         | 17 s    |
| 1000        | 22 s    |

After the ability ends, the tool's temporary enchant is removed and the ability enters a cooldown. The cooldown duration is shared across the dig-speed ability family and is configurable in `config.yml` under `Abilities.Cooldowns.Giga_Drill_Breaker` (default: 240 seconds).

| Property | Value |
|----------|-------|
| Unlock level | 50 |
| EnchantBuff (Efficiency bonus) | `Skills.General.Ability.EnchantBuff` (default: `5`) |

---

## Commands

| Command | Description |
|---------|-------------|
| `/excavation` | Display your Excavation skill stats and sub-skill information. |
| `/mctop excavation` | View the Excavation leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |
