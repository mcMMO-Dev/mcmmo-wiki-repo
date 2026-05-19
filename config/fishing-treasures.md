---
title: fishing_treasures.yml
description: Fishing Treasure Hunter, enchantment drop rates, and Shake drop configuration reference.
published: true
date: 2026-05-17T00:00:00.000Z
tags: config, fishing
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# fishing_treasures.yml

`fishing_treasures.yml` controls the complete loot tables for the Fishing skill. It has four distinct sections:

1. **`Fishing:`** — the item pool; items tagged with a rarity
2. **`Item_Drop_Rates:`** — per-tier (rank) % chance to receive an item of each rarity
3. **`Enchantments_Rarity:`** — which enchantments and levels can appear per rarity for enchanted books
4. **`Enchantment_Drop_Rates:`** — per-tier (rank) % chance to receive an enchanted book of each rarity
5. **`Shake:`** — mob-specific drop tables for the Shake sub-skill

Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/fishing_treasures.yml).

> Changes require a full server restart.
{.is-warning}

---

## Section 1: Fishing Item Pool

Each entry defines a single item and its rarity tag:

```yaml
Fishing:
    DIAMOND_SWORD:
        Amount: 1
        XP: 200
        Rarity: LEGENDARY
```

| Field | Description |
|-------|-------------|
| `Amount` | Quantity of the item given when it drops. |
| `XP` | Bonus Fishing XP awarded when this treasure drops. |
| `Rarity` | Rarity tier: `COMMON`, `UNCOMMON`, `RARE`, `EPIC`, `LEGENDARY`, or `MYTHIC`. |

### Default Rarity Groups

| Rarity | Items |
|--------|-------|
| `COMMON` | Leather armour, wood tools, copper armour, copper tools, lapis lazuli |
| `UNCOMMON` | Stone tools, copper tools, golden tools, golden armour, iron/gold ingots |
| `RARE` | Iron tools, bow, ender pearl, blaze rod, name tag |
| `EPIC` | Iron armour, ghast tear, 5× diamond |
| `LEGENDARY` | Diamond tools, diamond armour, nautilus shell, enchanted book, netherite scrap |
| `MYTHIC` | Netherite tools, netherite armour |

> For enchanted books, you can restrict which enchantments appear by adding an `Enchantments_Whitelist:` or `Enchantments_Blacklist:` block. See the commented example in the default file.
{.is-info}

---

## Section 2: Item Drop Rates

`Item_Drop_Rates` defines the percent chance to get an item of each rarity at each Treasure Hunter rank (Tier 1–8). The roll happens once per catch.

| Tier | COMMON | UNCOMMON | RARE | EPIC | LEGENDARY | MYTHIC |
|------|--------|---------|------|------|-----------|--------|
| 1 | 7.50% | 1.25% | 0.25% | 0.10% | 0.01% | 0.01% |
| 2 | 6.50% | 1.75% | 0.75% | 0.50% | 0.05% | 0.01% |
| 3 | 3.50% | 2.75% | 1.25% | 1.00% | 0.10% | 0.01% |
| 4 | 2.00% | 3.50% | 2.25% | 1.50% | 1.00% | 0.01% |
| 5 | 1.50% | 3.75% | 2.50% | 2.00% | 1.00% | 0.01% |
| 6 | 1.00% | 3.25% | 3.75% | 2.50% | 1.50% | 0.05% |
| 7 | 0.25% | 2.75% | 4.00% | 5.00% | 2.50% | 0.10% |
| 8 | 0.10% | 1.50% | 6.00% | 7.50% | 5.00% | 0.25% |

> At Tier 8, MYTHIC items still only have a 0.25% chance per catch. Keep this in mind when evaluating how "common" MYTHIC treasures actually are.
{.is-info}

---

## Section 3: Enchantments Rarity

`Enchantments_Rarity` defines which enchantments (and at which levels) are available in the enchanted book loot pool at each rarity. A higher number after the enchantment name means a higher enchantment level (e.g. `SHARPNESS: 4` = Sharpness IV).

| Rarity | Sample Enchantments |
|--------|-------------------|
| `COMMON` | Efficiency I, Unbreaking I, Fortune I, Protection I, Sharpness I, Power I |
| `UNCOMMON` | Efficiency II, Protection II, Looting I, Knockback I, Power II |
| `RARE` | Efficiency III, Unbreaking II, Fire Aspect I, Looting II, Power III |
| `EPIC` | Efficiency IV, Fortune II, Aqua Affinity, Thorns II, Flame, Power IV |
| `LEGENDARY` | Efficiency V, Unbreaking III, Fortune III, Silk Touch, Looting III, Infinity, Power V |
| `MYTHIC` | Same pool as LEGENDARY (highest-level enchants) |

---

## Section 4: Enchantment Drop Rates

`Enchantment_Drop_Rates` defines the per-tier (rank) percent chance to receive an enchanted book of each rarity on any given catch. This is a **separate roll** from the Item_Drop_Rates roll — a single catch can produce both a regular item and an enchanted book.

| Tier | COMMON | UNCOMMON | RARE | EPIC | LEGENDARY | MYTHIC |
|------|--------|---------|------|------|-----------|--------|
| 1 | 5.00% | 1.00% | 0.10% | 0.01% | 0.01% | 0.01% |
| 2 | 7.50% | 1.00% | 0.10% | 0.01% | 0.01% | 0.01% |
| 3 | 7.50% | 2.50% | 0.25% | 0.10% | 0.01% | 0.01% |
| 4 | 10.0% | 2.75% | 0.50% | 0.10% | 0.05% | 0.05% |
| 5 | 10.0% | 4.00% | 0.75% | 0.25% | 0.10% | 0.10% |
| 6 | 9.50% | 5.50% | 1.75% | 0.50% | 0.25% | 0.25% |
| 7 | 8.50% | 7.50% | 2.75% | 0.75% | 0.50% | 0.50% |
| 8 | 7.50% | 10.0% | 5.25% | 1.50% | 0.75% | 0.75% |

---

## Section 5: Shake

`Shake:` defines what each type of mob drops when a player uses the Shake sub-skill (fishing rod used on a hooked mob). Each mob has its own drop table:

```yaml
Shake:
    BLAZE:
        BLAZE_ROD:
            Amount: 1
            XP: 0
            Drop_Chance: 100.0
            Drop_Level: 0
```

| Field | Description |
|-------|-------------|
| `Amount` | Number of the item dropped. |
| `XP` | Bonus Fishing XP from this shake drop. |
| `Drop_Chance` | Percent chance (0–100) per shake. Multiple entries are evaluated independently. |
| `Drop_Level` | Minimum Fishing level (Standard mode) required. Multiplied ×10 for RetroMode. |

### Default Shake Drops (selected)

| Mob | Drops | Notes |
|-----|-------|-------|
| Blaze | Blaze Rod (100%) | |
| Cave Spider | Spider Eye (49%), String (49%), Cobweb (1%), Poison Potion (1%) | |
| Chicken | Feather (33%), Raw Chicken (33%), Egg (33%) | |
| Cow | Beef (49%), Leather (49%), Milk Bucket (2%) | |
| Creeper | Gunpowder (99%), Creeper Head (1%) | |
| Skeleton | Bone (49%), Arrow (49%), Bow (1%), Skeleton Skull (1%) | |
| Zombie | Rotten Flesh (98%), Iron Ingot (1%), Zombie Head (1%) | |
| Enderman | Ender Pearl (100%) | |

To add shake drops for additional mobs, add a new block using the Bukkit `EntityType` name as the key.

---

## Tips

- **Adjusting overall treasure frequency:** Change the percentages in `Item_Drop_Rates` for all tiers.
- **Adding a new item:** Add an entry under `Fishing:` with any valid material name and assign a rarity. The item will automatically be included in the rarity pool.
- **Tier count:** The number of tiers (8) matches the number of Treasure Hunter ranks and cannot be changed without modifying the source.
- **Enchanted books vs item drops:** These are two independent rolls. A single catch can yield a regular item, an enchanted book, both, or neither.
