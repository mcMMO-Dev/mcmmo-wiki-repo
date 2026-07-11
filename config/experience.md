---
title: experience.yml
description: mcMMO XP formula, multipliers, and per-action XP value configuration reference.
published: true
date: 2026-07-11T00:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# experience.yml

`experience.yml` is one of the most powerful config files in mcMMO. It controls the XP formula, multipliers, exploit-prevention flags, XP bar appearance, diminished returns, and the raw XP values for every in-game action. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/experience.yml).

> Changes require a full server restart.
{.is-warning}

---

## Early Game Boost

| Key | Default | Description |
|-----|---------|-------------|
| `EarlyGameBoost.Enabled` | `true` | Doubles XP gained while a player is at a very low skill level. Eases the early grind for new players. |

---

## Exploit Fix

These flags prevent common XP farming exploits. All default to `true` unless noted.

| Key | Default | Description |
|-----|---------|-------------|
| `ExploitFix.Combat.XPCeiling.Enabled` | `true` | Cap per-hit combat XP based on damage dealt. |
| `ExploitFix.Combat.XPCeiling.Damage_Limit` | `100` | Maximum damage value used for XP calculation (prevents one-shot farms). |
| `ExploitFix.COTWBreeding` | `true` | Prevent Call of the Wild summoned mobs from giving taming XP if immediately killed. |
| `ExploitFix.UnsafeEnchantments` | `false` | Block unsafe enchantment levels being applied via mcMMO. |
| `ExploitFix.Fishing` | `true` | Prevents many fishing location exploits. |
| `ExploitFix.EndermanEndermiteFarms` | `true` | Reduces XP from enderman/endermite exploits. |
| `ExploitFix.Acrobatics` | `true` | Prevent intentional fall XP farming with Roll (teleport cooldowns, same-spot lockouts, and related checks). |
| `ExploitFix.AcrobaticsDodgeXpFarming` | `true` | Stop a single mob from granting Dodge XP indefinitely. A mob grants Dodge XP for up to 6 dodges and recovers after 60 seconds without being dodged. |
| `ExploitFix.LavaStoneAndCobbleFarming` | `true` | Block lava-stone/cobble generator XP farms. |
| `ExploitFix.TreeFellerReducedXP` | `true` | Reduce XP from Tree Feller to prevent it being used for fast woodcutting XP. |
| `ExploitFix.PistonCheating` | `true` | Block piston-pushed block exploits. |
| `ExploitFix.SnowGolemExcavation` | `true` | Block snow golem snow farming for Excavation XP. |
| `ExploitFix.PreventArmorStandInteraction` | `true` | Prevent combat XP from attacking armor stands. |
| `ExploitFix.PreventMannequinInteraction` | `true` | Prevent combat XP from attacking mcMMO mannequins. |
| `ExploitFix.PreventPluginNPCInteraction` | `true` | Skip mcMMO processing for Citizens/NPC entities. |
| `ExploitFix.LimitTallPlantFarming` | `true` | Reduce XP from unnaturally tall plants (e.g. bonemeal-grown sugar cane). |

### Fishing Exploit Fix Options

| Key | Default | Description |
|-----|---------|-------------|
| `Fishing_ExploitFix_Options.MoveRange` | `3` | Blocks the player is allowed to move before fishing XP is revoked. |
| `Fishing_ExploitFix_Options.OverFishLimit` | `10` | Number of consecutive catches before XP drops significantly (over-fishing penalty). |

---

## Experience Bars

The XP bars appear as boss bars above the screen.

| Key | Default | Description |
|-----|---------|-------------|
| `Experience_Bars.Enable` | `true` | Master toggle for all XP bars. |
| `Experience_Bars.Update.Party` | `true` | Update bar when XP comes from a party member's action. |
| `Experience_Bars.Update.Passive` | `true` | Update bar for passive XP gains (smelting, brewing). |
| `Experience_Bars.ThisMayCauseLag.AlwaysUpdateTitlesWhenXPIsGained.Enable` | `false` | Refresh the title text on every XP gain. Expensive; leave off. |

Each skill can be individually toggled and styled:

```yaml
Experience_Bars:
    Acrobatics:
        Enable: true
        Color: PINK       # BLUE, GREEN, PINK, PURPLE, RED, WHITE, YELLOW
        BarStyle: SEGMENTED_6  # SOLID, SEGMENTED_6, SEGMENTED_10, SEGMENTED_12, SEGMENTED_20
```

---

## Experience Formula

Controls how much total XP is needed to reach each level.

| Key | Default | Description |
|-----|---------|-------------|
| `Experience_Formula.Curve` | `LINEAR` | XP formula type: `LINEAR` or `EXPONENTIAL`. |
| `Experience_Formula.Cumulative_Curve` | `false` | Use player power level (sum of all skills) instead of individual skill level for curve calculation. Very steep curve at high power levels. |

### Linear (Default)

$$\text{XP Required} = \text{base} + (\text{level} \times \text{multiplier})$$

| Key | Default |
|-----|---------|
| `Linear_Values.base` | `1020` |
| `Linear_Values.multiplier` | `20` |

### Exponential

$$\text{XP Required} = \text{multiplier} \times \text{level}^{\text{exponent}} + \text{base}$$

| Key | Default |
|-----|---------|
| `Exponential_Values.multiplier` | `0.1` |
| `Exponential_Values.exponent` | `1.80` |
| `Exponential_Values.base` | `2000` |

---

## Global Multipliers

| Key | Default | Description |
|-----|---------|-------------|
| `Experience_Formula.Multiplier.Global` | `1.0` | Multiply ALL XP gains across ALL skills. |
| `Experience_Formula.Multiplier.PVP` | `1.0` | Multiply XP gained from PvP kills. |
| `Experience_Formula.Eggs.Multiplier` | `0` | XP multiplier for mobs from spawn eggs (0 = no XP). |
| `Experience_Formula.Mobspawners.Multiplier` | `0` | XP multiplier for mobs from mob spawners. |
| `Experience_Formula.Nether_Portal.Multiplier` | `0` | XP multiplier for mobs that came through a nether portal. |
| `Experience_Formula.Breeding.Multiplier` | `1.0` | XP multiplier for player-bred animals. |

### Per-Skill Multipliers

```yaml
Skill_Multiplier:
    Mining: 1.0
    Fishing: 1.0
    # etc.
```

These are applied before the Global multiplier. Set a skill to `2.0` to double its XP rate independently.

### Custom XP Perk

| Key | Default | Description |
|-----|---------|-------------|
| `Experience_Formula.Custom_XP_Perk.Boost` | `1.25` | XP boost multiplier for players with the `mcmmo.perks.xp.customboost.<skillname>` permission. |

---

## Diminished Returns

Prevents XP grinding by reducing XP gains once a threshold is hit in a time window.

| Key | Default | Description |
|-----|---------|-------------|
| `Diminished_Returns.Enabled` | `false` | Enable the diminished returns system. |
| `Diminished_Returns.Guaranteed_Minimum_Percentage` | `0.05` | Minimum XP multiplier after diminishment (5% = players always get at least 5% of normal XP). Set to `0` to fully block XP after threshold. |
| `Diminished_Returns.Time_Interval` | `10` | Time window in minutes for the threshold. |
| `Diminished_Returns.Threshold.<Skill>` | `20000` | XP earned in `Time_Interval` minutes before diminishment kicks in (per skill). |

---

## XP Conversion

| Key | Default | Description |
|-----|---------|-------------|
| `Conversion.Exp_Modifier` | `1` | Divides existing player XP when running `/mcconvert experience`. Useful when switching from a higher-XP formula to a lower one. |

---

## Experience Values

These are the raw XP amounts awarded per action. They are multiplied by all applicable modifiers above before being applied.

### PvP

| Key | Default |
|-----|---------|
| `Experience_Values.PVP.Rewards` | `true` |

### Acrobatics

| Action | Default XP |
|--------|-----------|
| Dodge | 800 |
| Roll | 600 |
| Fall (no roll) | 600 |
| FeatherFall_Multiplier | ×2.0 (with Feather Falling boots) |

### Alchemy

| Stage | Default XP |
|-------|-----------|
| Stage 1 (base potion) | 666 |
| Stage 2 (+1 ingredient) | 1111 |
| Stage 3 (+1 ingredient +1 amplifier) | 1750 |
| Stage 4 (+1 ingredient +2 amplifiers) | 2250 |
| Stage 5 (amplifiers swapped) | 0 |

### Archery / Crossbows / Maces / Spears / Tridents

| Key | Default | Description |
|-----|---------|-------------|
| `Archery.Distance_Multiplier` | `0.025` | XP multiplier based on arrow flight distance. Longer shots = more XP. |

Combat XP for all weapon skills is based on damage dealt multiplied by the per-mob `Combat.Multiplier` (see below).

### Fishing

| Fish Type | Default XP |
|-----------|-----------|
| Cod | 100 |
| Salmon | 600 |
| Tropical Fish | 10000 |
| Pufferfish | 2400 |
| Shake | 50 |

### Excavation (per block)

| Block | XP | Block | XP |
|-------|----|-------|----|
| Dirt, Coarse Dirt, Sand, Gravel, etc. | 40 | Mud | 80 |
| Snow | 20 | Muddy Mangrove Roots | 90 |
| Soul Sand, Soul Soil | 40 | | |

### Herbalism (selected)

| Plant | XP | Plant | XP |
|-------|----|-------|----|
| Wheat, Carrot, Potato, Beetroot | 50 | Wither Rose | 500 |
| Poppy, Dandelion | 100 | Allium | 300 |
| Jungle/Ocean corals | 75–175 | Cactus | 30 |
| Moss Block | 150 | Sweet Berry Bush | 50 |

### Mining (selected)

| Block | XP | Block | XP |
|-------|----|-------|----|
| Coal Ore | 400 | Diamond Ore | 2400 |
| Iron Ore | 900 | Deepslate Diamond Ore | 3600 |
| Gold Ore | 1300 | Ancient Debris | 7777 |
| Copper Ore | 1400 | Reinforced Deepslate | 500 |
| Emerald Ore | 1000 | Obsidian | 150 |
| Nether Quartz Ore | 300 | Stone | 15 |

### Repair

Repair XP = `Base × MaterialMultiplier` where:

| Key | Default |
|-----|---------|
| `Repair.Base` | `1000.0` |
| `Repair.Wood` | `0.6` |
| `Repair.Stone` | `1.3` |
| `Repair.Copper` | `2.0` |
| `Repair.Iron` | `2.5` |
| `Repair.Gold` | `0.3` |
| `Repair.Diamond` | `5.0` |
| `Repair.Netherite` | `6.0` |
| `Repair.Leather` | `1.6` |
| `Repair.String` | `1.8` |
| `Repair.Other` | `1.5` |

### Smelting (per output item)

| Item | XP | Item | XP |
|------|----|------|----|
| Coal Ore | 10 | Iron Ore / Raw Iron | 25 |
| Redstone Ore | 15 | Gold Ore / Raw Gold | 35 |
| Nether Quartz Ore | 25 | Copper Ore / Raw Copper | 75 |
| Diamond Ore | 75 | Deepslate Diamond Ore | 140 |
| Ancient Debris | 200 | | |

### Taming

| Animal | XP | Animal | XP |
|--------|----|--------|---|
| Wolf | 250 | Llama | 1200 |
| Cat / Ocelot | 500 | Camel | 1300 |
| Horse / Donkey | 1000 | Sniffer | 1500 |
| Parrot | 1100 | Nautilus | 1700 |

### Woodcutting (selected)

| Wood | XP | Wood | XP |
|------|----|------|---|
| Oak Log | 70 | Jungle Log | 100 |
| Spruce Log | 80 | Mangrove Log | 95 |
| Birch Log | 90 | Pale Oak Log | 130 |
| Cherry Log | 105 | | |

### Combat Multipliers

All combat skills (Axes, Swords, Unarmed, Maces, Spears, Tridents, Archery, Crossbows) calculate XP as:

$$\text{XP} = \text{damage dealt} \times \text{mob multiplier}$$

Selected multipliers:

| Mob | Multiplier | Mob | Multiplier |
|-----|-----------|-----|-----------|
| Zombie, Slime | 2.0 | Creeper, Wither Skeleton | 4.0 |
| Spider, Cave Spider | 2.0 / 3.0 | Phantom, Breeze | 4.0 |
| Skeleton, Blaze | 3.0 | Piglin Brute | 4.5 |
| Enderman | 1.0 | Warden | 6.0 |
| Hoglin, Zoglin | 4.0 / 2.5 | Witch | 0.1 |
| Animals (default) | 1.0 | Snowman | 0.0 |
