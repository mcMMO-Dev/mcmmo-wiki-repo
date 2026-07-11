---
title: Repair
description: "Information about the Repair skill."
published: true
date: 2026-07-11T00:00:00.000Z
tags: repair, skills
editor: markdown
dateCreated: 2022-07-17T14:28:35.051Z
---

# Repair

The Repair skill allows you to restore the durability of tools and armour using the mcMMO Anvil -- an **iron block** placed in the world (not to be confused with the vanilla Minecraft anvil). Right-clicking the iron block while holding a repairable item consumes one repair material from your inventory and restores durability. Higher Repair skill unlocks Repair Mastery (bonus repair amount), Super Repair (chance to double the repair), and Arcane Forging (preserve enchantments through repair).

## At a glance

| | |
|---|---|
| **Category** | Utility / crafting |
| **Primary tool** | Iron Block (mcMMO Anvil) |
| **Super ability** | None |
| **Parent skill(s)** | None |
| **Child skill(s)** | Salvage (with Fishing) · Smelting (with Mining) |

> **Compared to vanilla:** the mcMMO Anvil (iron block) is *not* the vanilla anvil. The vanilla anvil still works as normal, it consumes XP levels and can preserve enchantments without a roll. The mcMMO Anvil instead consumes one repair material per use, can repair items at any level without an XP cost, and uses Arcane Forging rolls to preserve enchantments.
{.is-info}

## XP Gain

XP is awarded when a repair succeeds. The amount depends on how much durability was restored and the material tier of the item:

```
XP = (durability_restored / max_durability) x xp_multiplier x Base x material_modifier
```

`Base` defaults to 1000. `material_modifier` values (from `experience.yml` under `Repair`):

| Material tier | Modifier |
|---------------|---------|
| Gold | 0.3 |
| Wood | 0.6 |
| Stone | 1.3 |
| Other | 1.5 |
| Leather | 1.6 |
| String | 1.8 |
| Copper | 2.0 |
| Iron | 2.5 |
| Diamond | 5.0 |
| Netherite | 6.0 |

`xp_multiplier` is a per-item setting in `repair.vanilla.yml` (e.g., Shields default to 0.25).

## Repairable items

Each item below can be repaired at the mcMMO Anvil with the listed material. `XP mult.` is the item's `XpMultiplier` from `repair.vanilla.yml` (combined with the material modifier above to compute the repair XP). For vanilla items, mcMMO derives the repair material, max durability, and minimum quantity automatically; explicit values are shown where the YAML overrides them.

**Wooden tier** -- repair material: matching planks (Shield uses Oak Planks).

| Item | XP mult. | Notes |
|------|---------:|-------|
| Wooden Sword | 0.25 | |
| Wooden Spear | 0.25 | |
| Wooden Hoe | 0.25 | |
| Wooden Shovel | 0.16 | |
| Wooden Pickaxe | 0.5 | |
| Wooden Axe | 0.5 | |
| Shield | 0.25 | 6 planks per repair, 336 durability |

**Stone tier** -- repair material: Cobblestone.

| Item | XP mult. |
|------|---------:|
| Stone Sword / Spear / Hoe | 0.25 |
| Stone Shovel | 0.16 |
| Stone Pickaxe / Axe | 0.5 |

**Copper tier** -- repair material: Copper Ingot.

| Item | XP mult. |
|------|---------:|
| Copper Sword / Spear / Hoe | 0.3 |
| Copper Shovel | 0.2 |
| Copper Pickaxe / Axe | 0.6 |
| Copper Helmet / Chestplate / Leggings / Boots | 1.8 |

**Iron tier** -- repair material: Iron Ingot.

| Item | XP mult. |
|------|---------:|
| Iron Sword / Spear / Hoe | 0.5 |
| Iron Shovel | 0.3 |
| Iron Pickaxe / Axe | 1 |
| Shears | 0.5 |
| Flint and Steel | 0.3 |
| Iron Helmet / Chestplate / Leggings / Boots | 2 |

**Gold tier** -- repair material: Gold Ingot.

| Item | XP mult. |
|------|---------:|
| Golden Sword / Spear / Hoe | 4 |
| Golden Shovel | 2.6 |
| Golden Pickaxe / Axe | 8 |
| Golden Helmet / Chestplate / Leggings / Boots | 4 |

**Diamond tier** -- repair material: Diamond.

| Item | XP mult. |
|------|---------:|
| Diamond Sword / Spear | 0.5 |
| Diamond Hoe | 0.5 |
| Diamond Shovel | 0.3 |
| Diamond Pickaxe / Axe | 1 |
| Diamond Helmet / Chestplate / Leggings / Boots | 6 |

**Netherite tier** -- repair material: Netherite Ingot.

| Item | XP mult. |
|------|---------:|
| Netherite Sword / Spear | 0.6 |
| Netherite Hoe | 0.75 |
| Netherite Shovel | 0.4 |
| Netherite Pickaxe / Axe | 1.1 |
| Netherite Helmet / Chestplate / Leggings / Boots | 7 |

**Leather tier** -- repair material: Leather.

| Item | XP mult. |
|------|---------:|
| Leather Helmet / Chestplate / Leggings / Boots | 1 |

**String tier** -- repair material: String.

| Item | XP mult. | Notes |
|------|---------:|-------|
| Bow | 0.5 | |
| Fishing Rod | 0.5 | |
| Carrot on a Stick | 0.5 | |
| Crossbow | 0.5 | 3 string per repair, 326 durability |
| Warped Fungus on a Stick | 0.5 | 3 string per repair, 100 durability |

**Other repairables.**

| Item | XP mult. | Repair material | Per repair | Max durability |
|------|---------:|-----------------|-----------:|---------------:|
| Elytra | 3 | Phantom Membrane | 8 | 432 |
| Trident | 3 | Prismarine Crystals | 16 | 250 |
| Mace | 3 | Breeze Rod | 4 | (vanilla) |

> `MinimumLevel` for every vanilla item ships as `0`, so any player can repair them; server operators can raise the value per item in `repair.vanilla.yml`.
{.is-info}

## Usage

1. Place an iron block on the ground (this is the mcMMO Anvil).
2. Hold the item you want to repair.
3. Right-click the iron block. A confirmation prompt appears.
4. Right-click again within 3 seconds to confirm -- one repair material is consumed and durability is restored.

The confirming click must be made while holding the same item that triggered the prompt; switching items starts a new prompt, and the prompted item cannot be otherwise used while the confirmation is pending.

> The confirmation step can be disabled via `config.yml` (`Skills.Repair.Confirm_Required`).
{.is-info}

Items can only be repaired if your Repair skill is at or above the item's `MinimumLevel` configured in `repair.vanilla.yml`. A warning message is shown if your level is too low.

## Sub-Skills

### Repair Mastery

**Ranks:** 1 -- Unlocks at level 1

Repair Mastery passively increases the durability restored on every repair. The bonus scales linearly from 0 to a configurable maximum as your skill level rises.

| Skill level | Bonus repair |
|-------------|-------------|
| 1           | ~2 %        |
| 250         | ~50 %       |
| 500         | ~100 %      |
| 750         | ~150 %      |
| 1000+       | 200 % (cap) |

At level 1000 the repair amount is tripled (base + 200 % bonus). The cap and the level at which it is reached are configurable:

| Config key (under `Skills.Repair.RepairMastery`) | Default |
|--------------------------------------------------|---------|
| `MaxBonusPercentage` | `200.0` |
| `MaxBonusLevel.RetroMode` | `1000` |

---

### Super Repair

**Ranks:** 1 -- Unlocks at level 400

Super Repair is a passive sub-skill that gives a percentage chance to double the amount of durability repaired on each use. The chance scales linearly with skill level:

| Skill level | Chance |
|-------------|--------|
| 400         | 40 %   |
| 500         | 50 %   |
| 750         | 75 %   |
| 1000+       | 100 %  |

The maximum chance and the level at which it caps are configurable:

| Config key (under `Skills.Repair.SuperRepair`) | Default |
|------------------------------------------------|---------|
| `ChanceMax` | `100.0` |
| `MaxBonusLevel.RetroMode` | `1000` |

> Super Repair's doubling is applied after Repair Mastery's bonus, so at high levels a single repair can restore a very large amount of durability.
{.is-info}

---

### Arcane Forging

**Ranks:** 8

Arcane Forging is a passive sub-skill that gives enchanted items a chance to retain their enchantments when repaired at the mcMMO Anvil. Without Arcane Forging, all enchantments are stripped on repair.

For each enchantment on the item, two rolls are made:
1. **Keep roll** -- if this succeeds, the enchantment is carried forward to the downgrade check; if it fails, the enchantment is lost.
2. **Downgrade roll** (only if keep succeeds) -- if this succeeds, the enchantment is reduced by one level; if it fails, the enchantment is preserved at its current level (capped at `MaxEnchantLevel`).

**Chance values per rank (defaults):**

| Rank | Unlock level | Keep chance | Downgrade chance |
|------|-------------|-------------|-----------------|
| 1    | 100         | 10 %        | 75 %            |
| 2    | 250         | 20 %        | 50 %            |
| 3    | 350         | 30 %        | 40 %            |
| 4    | 500         | 40 %        | 30 %            |
| 5    | 650         | 50 %        | 25 %            |
| 6    | 750         | 50 %        | 20 %            |
| 7    | 850         | 60 %        | 15 %            |
| 8    | 1000        | 60 %        | 10 %            |

> Enchantments above the configured `MaxEnchantLevel` (default: 5) are capped to that level even on a successful keep roll. This prevents unsafe enchant stacking. To allow higher-tier enchants, raise `MaxEnchantLevel` or enable `ExploitFix.UnsafeEnchantments` in `experience.yml`.
{.is-info}

Enchant loss and downgrades can be disabled globally:

| Config key (under `Skills.Repair.ArcaneForging`) | Default |
|---------------------------------------------------|---------|
| `May_Lose_Enchants` | `true` |
| `Downgrades_Enabled` | `true` |
| `MaxEnchantLevel` | `5` |

Players with the `mcmmo.perks.repair.arcanebypass` permission always keep enchantments at full level.

---

## Commands

| Command | Description |
|---------|-------------|
| `/repair` | Display your Repair skill stats and sub-skill information. |
| `/mctop repair` | View the Repair leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Salvage](/skills/salvage.md): child skill that draws from Repair and Fishing
- [Smelting](/skills/smelting.md): child skill that draws from Repair and Mining
- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
