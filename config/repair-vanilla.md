---
title: repair.vanilla.yml
description: Vanilla item repair configuration reference for mcMMO Repair.
published: true
date: 2026-05-17T00:00:00.000Z
tags: config, repair
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# repair.vanilla.yml

`repair.vanilla.yml` defines which items can be repaired via the Repair skill anvil, what material is used to repair them, and the level/XP modifiers that apply. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/repair.vanilla.yml).

> Changes require a full server restart. For adding repairs for custom/modded items, see [Mods Support](/plugin-integration/plugin-support).
{.is-warning}

---

## Structure

Each entry under `Repairables:` follows this format:

```yaml
Repairables:
    SHIELD:
        MinimumLevel: 0
        XpMultiplier: .25
        ItemType: OTHER
        ItemMaterialCategory: WOOD
        RepairMaterial: OAK_PLANKS
        MinimumQuantity: 6
        MaximumDurability: 336
```

> For standard vanilla items (e.g. `DIAMOND_SWORD`) mcMMO auto-detects the repair material, item type, and durability from the material name. Those entries only need `MinimumLevel` and `XpMultiplier`. The full set of fields shown above is required for non-standard items such as the Shield, Elytra, and any custom/modded items.
{.is-info}

| Field | Description |
|-------|-------------|
| `MinimumLevel` | Minimum Repair skill level required to repair this item. |
| `XpMultiplier` | Multiplier applied to base Repair XP gained for this item. Higher = more XP per repair. |
| `ItemType` | `TOOL` or `ARMOR` — affects how Repair Mastery bonus is calculated. |
| `ItemMaterialCategory` | Material tier: `WOOD`, `STONE`, `LEATHER`, `IRON`, `GOLD`, `DIAMOND`, `NETHERITE`, `STRING`, `OTHER`. Determines base XP. |
| `RepairMaterial` | The Bukkit `Material` name of the item used on the anvil to repair it. |
| `MinimumQuantity` | Minimum number of repair materials consumed per repair attempt. |
| `MaximumDurability` | The item's maximum durability. Must match the actual Minecraft value. |

---

## Default Repairable Items

By default the file includes every repairable vanilla item grouped by material tier:

| Tier | Sample Items | Repair Material |
|------|-------------|----------------|
| Wood | Wooden sword, pickaxe, axe, shovel, hoe | `OAK_PLANKS` |
| Stone | Stone tools | `COBBLESTONE` |
| Leather | Leather helmet, chestplate, leggings, boots | `LEATHER` |
| Iron | Iron tools and armour | `IRON_INGOT` |
| Gold | Golden tools and armour | `GOLD_INGOT` |
| Diamond | Diamond tools and armour | `DIAMOND` |
| Netherite | Netherite tools and armour | `NETHERITE_INGOT` |

Other repairable items include the Elytra, Turtle Shell, Shield, Bow, Crossbow, Trident, and Fishing Rod.

---

## Tips

- **To change the repair material for an item**, change `RepairMaterial` to any Bukkit `Material` name. For example, make DIAMOND_SWORD repairable with `EMERALD`.
- **To require a skill level**, set `MinimumLevel` to the desired Standard mode level.
- **To grant more XP for repairing endgame gear**, increase `XpMultiplier` (e.g. `2.0` for netherite items).
- **To add a custom item**, create a new entry under `Repairables:` and fill in all required fields.
