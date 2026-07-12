---
title: Fishing
description: "Information about the Fishing skill."
published: true
date: 2026-07-12T00:00:00.000Z
tags: skills, fishing
editor: markdown
dateCreated: 2022-07-17T14:29:42.727Z
---

# Fishing

The Fishing skill enhances all fishing activities. Levelling Fishing unlocks faster bite times (Master Angler), ice-hole auto-creation (Ice Fishing), rare treasure drops from catches (Treasure Hunter), enchanted book drops (Magic Hunter), improved food healing from fish (Fisherman's Diet), and the ability to shake mobs to force item drops (Shake).

Fishing is also a **parent skill** of Salvage. Your Fishing level contributes to your Salvage level as: `floor((Repair + Fishing) / 2)`.

## At a glance

| | |
|---|---|
| **Category** | Gathering |
| **Primary tool** | Fishing Rod |
| **Super ability** | None |
| **Parent skill(s)** | None |
| **Child skill(s)** | Salvage (with Repair) |

## XP Gain

XP is earned each time a fish or treasure item is successfully caught. The amount depends on the catch type. Per-action XP values are configured in `experience.yml` under `Experience_Values.Fishing`.

| Catch | XP |
|-------|---:|
| Tropical Fish | 10000 |
| Pufferfish | 2400 |
| Salmon | 600 |
| Cod | 100 |
| Shake (per successful shake) | 50 |

Treasure catches award the base fish XP plus a bonus equal to the treasure's `XP` field in `fishing_treasures.yml` (default `200` for most fishing treasures).

## Loot System

Vanilla fishing loot and mcMMO Treasure Hunter loot are independent. When you catch something, vanilla first determines whether you get a fish, junk, or treasure. Then mcMMO makes a separate Treasure Hunter roll. It is possible to receive both a vanilla item and an mcMMO treasure from a single cast.

---

## Sub-Skills

### Fisherman's Diet

**Ranks:** 5

Fisherman's Diet increases the amount of hunger restored when eating fish. Each rank adds **+1 hunger point** restored on top of the food's base value. This sub-skill only affects the hunger bar; it does not change saturation.

| Rank | Unlock level | Bonus hunger restored |
|------|-------------|----------------------|
| 1 | 200 | +1 |
| 2 | 400 | +2 |
| 3 | 600 | +3 |
| 4 | 800 | +4 |
| 5 | 1000 | +5 |

---

### Ice Fishing

**Ranks:** 1 -- Unlocks at level 50

Ice Fishing automatically breaks a 3x3 area of ice blocks directly beneath your fishing bobber when it lands, creating an open water hole. This allows fishing in frozen biomes without needing to manually clear ice. The bobber is then automatically recast in the new water.

---

### Magic Hunter

**Ranks:** 1 -- Unlocks at level 200

Magic Hunter enables enchanted books to appear in the Treasure Hunter loot pool. It requires Treasure Hunter to be unlocked (rank 1 at level 1). When a Treasure Hunter roll selects an enchanted book, mcMMO performs a second roll against the enchantment pool for the same rarity tier.

**Enchantment drop chances by rank and rarity (`fishing_treasures.yml` → `Enchantment_Drop_Rates`):**

| Tier (rank) | Common | Uncommon | Rare | Epic | Legendary | Mythic |
|------------:|-------:|---------:|-----:|-----:|----------:|-------:|
| 1 | 5.00 | 1.00 | 0.10 | 0.01 | 0.01 | 0.01 |
| 2 | 7.50 | 1.00 | 0.10 | 0.01 | 0.01 | 0.01 |
| 3 | 7.50 | 2.50 | 0.25 | 0.10 | 0.01 | 0.01 |
| 4 | 10.00 | 2.75 | 0.50 | 0.10 | 0.05 | 0.05 |
| 5 | 10.00 | 4.00 | 0.75 | 0.25 | 0.10 | 0.10 |
| 6 | 9.50 | 5.50 | 1.75 | 0.50 | 0.25 | 0.25 |
| 7 | 8.50 | 7.50 | 2.75 | 0.75 | 0.50 | 0.50 |
| 8 | 7.50 | 10.00 | 5.25 | 1.50 | 0.75 | 0.75 |

**Available enchantments per rarity tier** (`fishing_treasures.yml` → `Enchantments_Rarity`, level shown in parentheses):

| Rarity | Enchantments (max level) |
|--------|--------------------------|
| Common | Efficiency I, Unbreaking I, Fortune I, Protection I, Fire Protection I, Feather Falling I, Blast Protection I, Projectile Protection I, Respiration I, Thorns I, Sharpness I, Smite I, Bane of Arthropods I, Power I |
| Uncommon | Efficiency II, Protection II, Fire Protection II, Feather Falling II, Blast Protection II, Projectile Protection II, Sharpness II, Smite II, Bane of Arthropods II, Knockback I, Looting I, Power II, Punch I |
| Rare | Efficiency III, Unbreaking II, Protection III, Fire Protection III, Feather Falling III, Blast Protection III, Projectile Protection III, Respiration II, Sharpness III, Smite III, Bane of Arthropods III, Fire Aspect I, Looting II, Power III |
| Epic | Efficiency IV, Fortune II, Aqua Affinity I, Thorns II, Sharpness IV, Smite IV, Bane of Arthropods IV, Power IV, Flame I |
| Legendary | Efficiency V, Unbreaking III, Fortune III, Protection IV, Fire Protection IV, Feather Falling IV, Blast Protection IV, Projectile Protection IV, Respiration III, Aqua Affinity I, Thorns III, Sharpness V, Smite V, Bane of Arthropods V, Knockback II, Fire Aspect II, Looting III, Silk Touch I, Power V, Punch II, Infinity I |
| Mythic | Same pool as Legendary (max-level enchantments). |

---

### Master Angler

**Ranks:** 8

Master Angler reduces the minimum and maximum wait time for a bite. Each rank reduces both the minimum and maximum tick wait by a configurable amount per rank (default: 10 ticks per rank for min-wait and 30 ticks per rank for max-wait). Being in a **boat** grants an additional flat reduction on top of the rank-based reduction.

Vanilla Lure enchantment is properly accounted for: mcMMO applies the Lure bonus manually at any Lure level (1 or higher) to avoid a Minecraft engine bug with Lure levels above 3.

| Rank | Unlock level |
|------|-------------|
| 1 | 1 |
| 2 | 200 |
| 3 | 300 |
| 4 | 400 |
| 5 | 600 |
| 6 | 700 |
| 7 | 800 |
| 8 | 900 |

**Config keys** (`advanced.yml` under `Skills.Fishing.MasterAngler`):

| Key | Default | Description |
|-----|---------|-------------|
| `Tick_Reduction_Per_Rank.Min_Wait` | `10` | Ticks of min-wait reduction per rank |
| `Tick_Reduction_Per_Rank.Max_Wait` | `30` | Ticks of max-wait reduction per rank |
| `Boat_Tick_Reduction.Min_Wait` | `10` | Additional ticks of min-wait reduction when in a boat |
| `Boat_Tick_Reduction.Max_Wait` | `30` | Additional ticks of max-wait reduction when in a boat |
| `Tick_Reduction_Caps.Min_Wait` | `40` | Minimum allowed min-wait tick floor |
| `Tick_Reduction_Caps.Max_Wait` | `100` | Minimum allowed max-wait tick floor |

---

### Treasure Hunter

**Ranks:** 8

Treasure Hunter gives a chance to catch bonus treasure items instead of (or in addition to) regular fish. The treasure pool and drop chances are defined in `fishing_treasures.yml`. Higher ranks unlock rarer treasures and increase drop chances.

| Rank | Unlock level |
|------|-------------|
| 1 | 1 |
| 2 | 250 |
| 3 | 350 |
| 4 | 500 |
| 5 | 650 |
| 6 | 750 |
| 7 | 850 |
| 8 | 1000 |

**Treasure drop chances by rank and rarity (`fishing_treasures.yml` → `Item_Drop_Rates`):**

Each catch makes a single 0-100 roll (modified by the rod's Luck of the Sea enchantment). Rarities are checked from rarest to most common (Mythic, Legendary, Epic, Rare, Uncommon, Common); the first rarity whose drop chance covers the roll is the one that drops. Values below are percent chance.

| Tier (rank) | Common | Uncommon | Rare | Epic | Legendary | Mythic |
|------------:|-------:|---------:|-----:|-----:|----------:|-------:|
| 1 | 7.50 | 1.25 | 0.25 | 0.10 | 0.01 | 0.01 |
| 2 | 6.50 | 1.75 | 0.75 | 0.50 | 0.05 | 0.01 |
| 3 | 3.50 | 2.75 | 1.25 | 1.00 | 0.10 | 0.01 |
| 4 | 2.00 | 3.50 | 2.25 | 1.50 | 1.00 | 0.01 |
| 5 | 1.50 | 3.75 | 2.50 | 2.00 | 1.00 | 0.01 |
| 6 | 1.00 | 3.25 | 3.75 | 2.50 | 1.50 | 0.05 |
| 7 | 0.25 | 2.75 | 4.00 | 5.00 | 2.50 | 0.10 |
| 8 | 0.10 | 1.50 | 6.00 | 7.50 | 5.00 | 0.25 |

> As rank increases, Common drops become rarer and high-rarity drops become more common. The total chance of catching any treasure on a cast is the sum of all six rarity values for your tier.
{.is-info}

The pool of items in each rarity tier (`Fishing:` section of `fishing_treasures.yml`) is fully customisable per server. Default Common items include leather armour, wooden tools, and lapis; Uncommon includes stone and copper tools, golden armour, and iron/gold ingots; Rare includes iron tools, bow, ender pearl, blaze rod, and name tag; Epic includes iron armour and ghast tear; Legendary and Mythic include the rarest fish, music discs, totems, and similar high-value items.

---

### Shake

**Ranks:** 8 -- Unlocks at level 150

Shake allows you to cast your fishing line at a mob that is in water and force it to drop its held item (the same drops as using the Looting enchantment on that mob type). Each successful shake also deals a small amount of damage to the mob (about a quarter of its maximum health, at least 1 and capped at 10), so a mob can usually be shaken about four times before it dies. The proc chance per rank is a fixed value from the config.

| Rank | Unlock level | Proc chance |
|------|-------------|-------------|
| 1 | 150 | 15% |
| 2 | 200 | 20% |
| 3 | 250 | 25% |
| 4 | 300 | 35% |
| 5 | 400 | 45% |
| 6 | 500 | 55% |
| 7 | 600 | 65% |
| 8 | 700 | 75% |

**Config keys** (`advanced.yml` under `Skills.Fishing.ShakeChance`):

| Key | Default | Description |
|-----|---------|-------------|
| `Rank_N` | (see table) | Proc chance per rank |

**Vanilla XP multiplier** (`advanced.yml` under `Skills.Fishing.VanillaXPMultiplier`):

Each Shake rank also multiplies vanilla fishing XP orb drops:

| Rank | Vanilla XP multiplier |
|------|-----------------------|
| 1 | x1 |
| 2 | x2 |
| 3 | x3 |
| 4 | x3 |
| 5 | x4 |
| 6 | x4 |
| 7 | x5 |
| 8 | x5 |

**Shake drops per mob** (`fishing_treasures.yml` → `Shake`):

When a Shake roll succeeds on an eligible mob, one item is selected from that mob's drop pool using the per-item drop chances below. Per-mob totals sum to 100 % (or just under 100 % for mobs that occasionally drop nothing).

| Mob | Item (drop chance) |
|-----|--------------------|
| Blaze | Blaze Rod (100 %) |
| Cave Spider | Spider Eye (49 %), String (49 %), Cobweb (1 %), Poison Potion (1 %) |
| Chicken | Feather (33.3 %), Chicken (33.3 %), Egg (33.3 %) |
| Cow | Beef (49 %), Leather (49 %), Milk Bucket (2 %) |
| Creeper | Gunpowder (99 %), Creeper Head (1 %) |
| Enderman | Ender Pearl (100 %) |
| Ghast | Gunpowder (50 %), Ghast Tear (50 %) |
| Horse | Leather (99 %), Saddle (1 %) |
| Iron Golem | Poppy (85 %), Iron Ingot (12 %), Pumpkin (3 %) |
| Magma Cube | Magma Cream (100 %) |
| Mooshroom | Leather (30 %), Beef (30 %), Red Mushroom ×2 (30 %), Milk Bucket (5 %), Mushroom Stew (5 %) |
| Pig | Porkchop (100 %) |
| Pig Zombie / Zombified Piglin | Rotten Flesh (50 %), Gold Nugget (50 %) |
| Sheep | White Wool ×3 (100 %) |
| Shulker | Purpur Block (75 %), Shulker Shell (25 %) |
| Skeleton | Bone (49 %), Arrow ×2 (49 %), Skeleton Skull (2 %) |
| Slime | Slime Ball (100 %) |
| Snow Golem | Snowball ×2 (97 %), Pumpkin (3 %) |
| Spider | Spider Eye (50 %), String (50 %) |
| Squid | Ink Sac (100 %) |
| Witch | Glowstone Dust / Gunpowder / Redstone / Spider Eye / Stick / Sugar (15 % each), Glass Bottle (7 %), Splash Potions of Healing / Fire Resistance / Speed (1 % each) |
| Wither Skeleton | Bone (49 %), Coal ×2 (49 %), Wither Skeleton Skull (2 %) |
| Zombie | Rotten Flesh (98 %), Zombie Head (2 %) |

> Each successful shake deals up to 10 damage (about a quarter of the mob's maximum health), so a mob survives roughly four shakes. Items beyond those listed here can be added via `fishing_treasures.yml`.
{.is-info}

---

## Commands

| Command | Description |
|---------|-------------|
| `/fishing` | Display your Fishing skill stats and sub-skill information. |
| `/mctop fishing` | View the Fishing leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Salvage](/skills/salvage): child skill that draws from Fishing and Repair
- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
