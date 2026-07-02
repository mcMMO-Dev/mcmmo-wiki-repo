---
title: Woodcutting
description: "Information about the Woodcutting skill."
published: true
date: 2024-11-24T01:42:15.334Z
tags: skills, woodcutting
editor: markdown
dateCreated: 2022-07-17T14:29:42.727Z
---

# Woodcutting

The Woodcutting skill rewards players for chopping wood. It grants double drops (Harvest Lumber), triple drops (Clean Cuts), instant leaf destruction (Leaf Blower), an active ability to fell entire trees (Tree Feller), and sapling or vanilla XP orb drops during Tree Feller (Knock on Wood).

## At a glance

| | |
|---|---|
| **Category** | Gathering |
| **Primary tool** | Axe |
| **Super ability** | Tree Feller |
| **Parent skill(s)** | None |
| **Child skill(s)** | None |

## XP Gain

XP is earned by breaking log, wood, and a few related blocks with an axe. Per-block XP values are configured in `experience.yml` under `Experience_Values.Woodcutting`. The default values are listed below.

### Logs and wood

| Wood type | Log | Stripped Log | Wood (bark) | Stripped Wood |
|-----------|----:|-------------:|------------:|--------------:|
| Oak | 70 | 70 | 70 | 70 |
| Spruce | 80 | 80 | 70 | 80 |
| Birch | 90 | 90 | 70 | 90 |
| Jungle | 100 | 100 | 70 | 100 |
| Acacia | 90 | 90 | 70 | 90 |
| Dark Oak | 90 | 90 | 70 | 90 |
| Cherry | 105 | 105 | 105 | 70 |
| Mangrove | 95 | 110 | 80 |  |
| Pale Oak | 130 | 130 | 110 | 90 |
| Crimson (Stem / Hyphae) | 35 | 50 | 50 | 50 |
| Warped (Stem / Hyphae) | 35 | 50 | 50 | 50 |

### Other Woodcutting blocks

| Block | XP |
|-------|---:|
| Shroomlight | 100 |
| Mushroom Stem | 80 |
| Red Mushroom Block | 70 |
| Brown Mushroom Block | 70 |
| Mangrove Roots | 10 |
| Nether Wart Block | 1 |
| Warped Wart Block | 1 |

> Leaf blocks broken via Leaf Blower do **not** grant Woodcutting XP. Only logs, wood, and the blocks above grant XP.
{.is-info}

## Sub-Skills

### Harvest Lumber

**Ranks:** 1, Unlocks at level 1

Harvest Lumber is a passive sub-skill that grants a chance to receive a double drop of the wood you break. The chance scales linearly from 0% at level 0 to **100%** at level 1000.

**Config keys** (`advanced.yml` under `Skills.Woodcutting.HarvestLumber`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `100.0` | Maximum double-drop chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which max chance is reached |

---

### Clean Cuts

**Ranks:** 1, Unlocks at level 1000

Clean Cuts is a passive sub-skill that grants a chance to receive a **triple drop** of the wood you break. It rolls independently from Harvest Lumber; if Clean Cuts procs, the player receives two bonus logs (for three total). If Harvest Lumber procs but Clean Cuts does not, the player receives one bonus log (for two total).

The chance scales linearly from 0% at level 0 to **50%** at level 10,000.

**Config keys** (`advanced.yml` under `Skills.Woodcutting.CleanCuts`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `50.0` | Maximum triple-drop chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `10000` | Skill level at which max chance is reached |

---

### Leaf Blower

**Ranks:** 3

Leaf Blower allows players to instantly break leaf blocks and other non-wood tree parts (such as bee nests, shroomlights, and similar) while holding an axe. No XP is awarded for leaf blocks.

| Rank | Unlock level |
|------|-------------|
| 1 | 150 |
| 2 | 350 |
| 3 | 650 |

---

### Tree Feller

**Ranks:** 5, Unlocks at level 50

Tree Feller is an active ability that must be armed by right-clicking with an axe while not looking at a block. When active, breaking any log block causes the entire connected tree (all attached logs and non-wood tree parts) to be felled at once. XP is awarded for each log block removed.

Tree Feller causes extra durability damage to the axe proportional to the number of blocks felled. If the axe would break during Tree Feller, it splinters at the first block and Tree Feller is cancelled.

Duration scales with your Woodcutting level, starting at 3 seconds at level 50 and gaining 1 second every additional 50 levels, up to a default maximum of 1000 seconds.

| Woodcutting Level | Duration |
|------------------:|---------:|
| 50                | 3s       |
| 100               | 4s       |
| 200               | 6s       |
| 500               | 12s      |
| 1000              | 22s      |
| 2000              | 42s      |

| Property | Key | Default | Description |
|----------|-----|---------|-------------|
| Unlock level | `skillranks.yml` → `Woodcutting.TreeFeller.RetroMode.Rank_1` | `50` | Minimum skill level to unlock this ability |
| Cooldown | `config.yml` → `Abilities.Cooldowns.Tree_Feller` | `240s` | Seconds before the ability can be activated again |
| Max duration | `config.yml` → `Abilities.Max_Seconds.Tree_Feller` | `0` (no cap) | Per-ability duration ceiling in seconds. Only takes effect if lower than the global duration cap; 0 disables this cap entirely |
| Global duration cap | `advanced.yml` → `Skills.General.Ability.Length.RetroMode.CapLevel` | `1000s` | Maximum duration for all super abilities |

Higher ranks increase the maximum number of blocks that can be felled in one use (the tree feller threshold is also configurable in `config.yml`).

| Rank | Unlock level |
|------|-------------|
| 1 | 50 |
| 2 | 250 |
| 3 | 500 |
| 4 | 750 |
| 5 | 1000 |

**Config keys** (`config.yml` under `Abilities`):

| Key | Default | Description |
|-----|---------|-------------|
| `Limits.Tree_Feller_Threshold` | `1000` | Maximum number of blocks Tree Feller can fell in a single use |
| `Cooldowns.Tree_Feller` | `240` | Cooldown in seconds before Tree Feller can be used again |

---

### Knock on Wood

**Ranks:** 2, Unlocks at level 300

Knock on Wood triggers during Tree Feller. When active:

- **Rank 1 (level 300):** Leaf blocks removed during Tree Feller have a chance to drop saplings and propagules.
- **Rank 2 (level 600):** Additionally, there is a 10% chance per non-wood block removed for a random number of vanilla XP orbs (1–100) to spawn at the block''s location. Requires `Add_XP_Orbs_To_Drops: true` in `advanced.yml` (default: `true`).

| Rank | Unlock level | Effect |
|------|-------------|--------|
| 1 | 300 | Saplings drop from leaves during Tree Feller |
| 2 | 600 | Also spawns vanilla XP orbs during Tree Feller |

**Config keys** (`advanced.yml` under `Skills.Woodcutting.TreeFeller.Knock_On_Wood`):

| Key | Default | Description |
|-----|---------|-------------|
| `Add_XP_Orbs_To_Drops` | `true` | Enables vanilla XP orb spawning at Rank 2 |

---

## Commands

| Command | Description |
|---------|-------------|
| `/woodcutting` | Display your Woodcutting skill stats and sub-skill information. |
| `/mctop woodcutting` | View the Woodcutting leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
- [Configuration](/config)
