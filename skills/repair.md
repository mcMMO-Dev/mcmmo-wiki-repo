---
title: Repair
description: "Information about the Repair skill."
published: true
date: 2024-11-24T01:41:51.767Z
tags: repair, skills
editor: markdown
dateCreated: 2022-07-17T14:28:35.051Z
---

# Repair

The Repair skill allows you to restore the durability of tools and armour using the mcMMO Anvil -- an **iron block** placed in the world (not to be confused with the vanilla Minecraft anvil). Right-clicking the iron block while holding a repairable item consumes one repair material from your inventory and restores durability. Higher Repair skill unlocks Repair Mastery (bonus repair amount), Super Repair (chance to double the repair), and Arcane Forging (preserve enchantments through repair).

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

## Usage

1. Place an iron block on the ground (this is the mcMMO Anvil).
2. Hold the item you want to repair.
3. Right-click the iron block. A confirmation prompt appears.
4. Right-click again within 3 seconds to confirm -- one repair material is consumed and durability is restored.

> The confirmation step can be disabled via `general.yml` (`Repair.Confirm_Required`).
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
1. **Keep roll** -- the enchantment is preserved at its current level (capped at `MaxEnchantLevel`).
2. **Downgrade roll** (if keep fails) -- the enchantment is reduced by one level.
3. If both rolls fail, the enchantment is lost.

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
