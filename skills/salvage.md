---
title: Salvage
description: "Information about the Salvage skill."
published: true
date: 2024-11-24T01:59:07.533Z
tags: salvage, skills
editor: markdown
dateCreated: 2024-11-24T01:59:07.533Z
---

# Salvage

The Salvage skill lets you break down tools and armor at a Salvage Anvil (a **gold block**) to recover base materials and potentially extract enchantments as an enchanted book. Higher ranks of Scrap Collector recover more materials, while Arcane Salvage gives an increasing chance to preserve enchantments.

> Salvage is a **child skill** of Repair and Fishing. Your Salvage level equals the average of your Repair and Fishing levels: `Salvage level = floor((Repair + Fishing) / 2)`. You cannot level Salvage directly -- improve Repair and Fishing to increase it.
{.is-info}

## At a glance

| | |
|---|---|
| **Category** | Utility / crafting (child skill) |
| **Primary tool** | Gold Block (Salvage Anvil) |
| **Super ability** | None |
| **Parent skill(s)** | Repair + Fishing |
| **Child skill(s)** | None |

> **Compared to vanilla:** the vanilla Grindstone strips enchantments and returns a small amount of XP, but never returns any of the item's crafting materials. The mcMMO Salvage Anvil (gold block) instead returns a portion of the original crafting materials and can optionally extract one enchantment as an enchanted book.
{.is-info}

## Usage

Place a gold block to create a Salvage Anvil. Hold the item to salvage in your main hand and right-click the anvil. You will be prompted to confirm; right-click again within 3 seconds to proceed.

> Items that are unbreakable or have custom model data (when disallowed by config) cannot be salvaged.
{.is-warning}

## Sub-Skills

### Scrap Collector

**Ranks:** 8 -- Unlocks at level 1

Scrap Collector determines the maximum number of base materials you can recover from a salvage. The actual yield is also scaled by the item's remaining durability -- a fully repaired item yields the most materials; a heavily damaged item yields fewer.

**Formula:** `yield = floor(maxQuantity x percentDurabilityRemaining)`, capped at the Scrap Collector limit.

| Rank | Unlock level | Max materials recoverable |
|------|-------------|--------------------------|
| 1 | 1 | 1 |
| 2 | 100 | 4 |
| 3 | 150 | 6 |
| 4 | 200 | 8 |
| 5 | 250 | 10 |
| 6 | 300 | 12 |
| 7 | 350 | 14 |
| 8 | 400 | 16 |

> Rank 1 always yields exactly 1 material regardless of durability. Ranks 2 and higher use `rank x 2` as the cap.
{.is-info}

---

### Arcane Salvage

**Ranks:** 8 -- Unlocks at level 100

Arcane Salvage gives a chance to extract enchantments from a salvaged item and produce an enchanted book. Without Arcane Salvage, enchantments are always lost on salvage. With it, each enchantment on the item is independently rolled for one of three outcomes:

| Outcome | Description |
|---------|-------------|
| **Full extract** | The enchantment is preserved at its original level in the enchanted book. |
| **Partial extract** | The enchantment is preserved but downgraded by one level. |
| **Lost** | The enchantment is not recovered. |

If all enchantments are lost, no enchanted book is produced and the player is notified.

The maximum enchantment level kept or downgraded to is capped at `MaxEnchantLevel` (default 5) unless unsafe enchantments are enabled.

| Rank | Unlock level | Full extract chance | Partial extract chance |
|------|-------------|--------------------|-----------------------|
| 1 | 100 | 2.5% | 2.0% |
| 2 | 250 | 5.0% | 2.5% |
| 3 | 350 | 7.5% | 5.0% |
| 4 | 500 | 10.0% | 7.5% |
| 5 | 650 | 12.5% | 10.0% |
| 6 | 750 | 17.5% | 12.5% |
| 7 | 850 | 25.0% | 15.0% |
| 8 | 1000 | 32.5% | 17.5% |

**Config keys** (`advanced.yml` under `Skills.Salvage.ArcaneSalvage`):

| Key | Default | Description |
|-----|---------|-------------|
| `EnchantLossEnabled` | `true` | Whether enchantments can be lost entirely |
| `EnchantDowngradeEnabled` | `true` | Whether enchantments can be downgraded |
| `MaxEnchantLevel` | `5` | Maximum level preserved or downgraded to |
| `ExtractFullEnchant.Rank_N` | (see table) | Full extract chance per rank |
| `ExtractPartialEnchant.Rank_N` | (see table) | Partial extract chance per rank |

> Players with the `mcmmo.perks.salvage.arcanebypass` permission always extract enchantments at full level without any chance of loss.
{.is-info}

---

## Commands

| Command | Description |
|---------|-------------|
| `/salvage` | Display your Salvage skill stats and sub-skill information. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Repair](skills/repair.md): parent skill
- [Fishing](skills/fishing.md): parent skill
- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
