---
title: Herbalism
description: "Information about the Herbalism skill."
published: true
date: 2024-11-24T01:41:48.891Z
tags: skills, herbalism
editor: markdown
dateCreated: 2022-07-17T14:29:42.727Z
---

# Herbalism

The Herbalism skill rewards players for growing and harvesting plants. Levelling Herbalism unlocks double and triple drop bonuses (Double Drops, Verdant Bounty), improved food healing (Farmer's Diet), automatic crop replanting (Green Thumb), an active ability to convert blocks into farmland (Green Terra), hidden treasure from grass and flowers (Hylian Luck), and mushroom conversion (Shroom Thumb).

## XP Gain

XP is earned by breaking herb and plant blocks (wheat, carrots, potatoes, beetroot, nether wart, cactus, cocoa, sugar cane, mushrooms, flowers, etc.). XP values are determined per material in `experience.yml`. Only mature crops award the full XP value; immature crops award reduced or no XP depending on configuration.

## Sub-Skills

### Double Drops

**Ranks:** 1 -- Unlocks at level 1

Double Drops is a passive sub-skill that grants a chance to receive an extra drop from any herbalism-eligible block you break. The chance scales linearly from 0% at level 0 to **100%** at level 1000.

**Config keys** (`advanced.yml` under `Skills.Herbalism.DoubleDrops`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `100.0` | Maximum double-drop chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which max chance is reached |

---

### Verdant Bounty

**Ranks:** 1 -- Unlocks at level 1000

Verdant Bounty is a passive sub-skill that grants a chance to receive a **second** extra drop (a triple drop) from herbalism-eligible blocks, in addition to the Double Drops bonus. It rolls independently; if both proc, three items drop instead of one. The chance scales from 0% to **50%** at level 10000.

> Verdant Bounty scales all the way to level **10,000** in Retro mode -- by far the longest progression of any Herbalism sub-skill. This is intentional: it provides long-term endgame progression for dedicated herbalism players.
{.is-info}

**Config keys** (`advanced.yml` under `Skills.Herbalism.VerdantBounty`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `50.0` | Maximum triple-drop chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `10000` | Skill level at which max chance is reached |

---

### Farmer's Diet

**Ranks:** 5

Farmer's Diet increases the amount of hunger restored when eating food. Each rank adds **+1 hunger point** restored on top of the food's base value.

| Rank | Unlock level | Bonus hunger restored |
|------|-------------|----------------------|
| 1 | 200 | +1 |
| 2 | 400 | +2 |
| 3 | 600 | +3 |
| 4 | 800 | +4 |
| 5 | 1000 | +5 |

---

### Green Thumb

**Ranks:** 4

Green Thumb is a passive proc that automatically replants a mature crop as a young plant immediately after breaking it, consuming one seed from the player's inventory. It requires the player to hold a hoe (or an axe for Cocoa Beans).

Supported crops: Wheat, Carrots, Potatoes, Beetroot, Nether Wart, Cocoa Beans, Torchflower, Sweet Berry Bush.

The proc chance scales linearly from 0% at level 0 to **100%** at level 1000. Green Thumb always activates (no chance roll) while Green Terra is active.

| Rank | Unlock level |
|------|-------------|
| 1 | 250 |
| 2 | 500 |
| 3 | 750 |
| 4 | 1000 |

**Config keys** (`advanced.yml` under `Skills.Herbalism.GreenThumb`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `100.0` | Maximum proc chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which max chance is reached |

---

### Green Terra

**Ranks:** 1 -- Unlocks at level 50

Green Terra is an active ability that must be armed by right-clicking with a hoe while not looking at a block. When active, interacting with dirt blocks converts them into farmland, and Green Thumb procs automatically without a chance roll for the duration.

---

### Hylian Luck

**Ranks:** 0 (passive, no rank unlock required)

Hylian Luck gives a chance to find hidden treasures by breaking grass blocks, dead bushes, ferns, and similar vegetation with a sword or other eligible tool. The treasure pool is defined in `treasures.yml` under `Hylian_Luck`. The chance scales from 0% to **10%** at level 1000.

When Hylian Luck procs, the block is broken and a treasure item is spawned instead.

**Config keys** (`advanced.yml` under `Skills.Herbalism.HylianLuck`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `10.0` | Maximum proc chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which max chance is reached |

---

### Shroom Thumb

**Ranks:** 0 (passive, no rank unlock required)

Shroom Thumb allows a player to convert a dirt or grass block into a mycelium block by right-clicking it while holding one Brown Mushroom and one Red Mushroom. Both mushrooms are consumed on use. The chance of success scales from 0% to **50%** at level 1000.

If the conversion fails, the player is notified and the mushrooms are still consumed.

**Config keys** (`advanced.yml` under `Skills.Herbalism.ShroomThumb`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `50.0` | Maximum success chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which max chance is reached |

---

## Commands

| Command | Description |
|---------|-------------|
| `/herbalism` | Display your Herbalism skill stats and sub-skill information. |
| `/mctop herbalism` | View the Herbalism leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |
