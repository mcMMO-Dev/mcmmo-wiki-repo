---
title: salvage.vanilla.yml
description: Vanilla item salvage configuration reference for mcMMO Salvage.
published: true
date: 2026-05-17T00:00:00.000Z
tags: config, salvage
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# salvage.vanilla.yml

`salvage.vanilla.yml` defines which items can be salvaged at the Salvage anvil, what material they yield, and how much of it. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/salvage.vanilla.yml).

> Changes require a full server restart. For adding salvage entries for custom/modded items, see [Mods Support](/plugin-integration/plugin-support).
{.is-warning}

---

## Structure

Each entry under `Salvageables:` follows this format:

```yaml
Salvageables:
    DIAMOND_SWORD:
        MinimumLevel: 50
        XpMultiplier: .5
        MaximumQuantity: 2
```

> For craftable vanilla items (tools, armour) mcMMO auto-detects the salvage material from the crafting recipe — no `SalvageMaterial` field is needed. For non-craftable items (e.g. Elytra), you must specify `SalvageMaterial` explicitly.
{.is-info}

> By default, **diamond items require level 50** and **netherite items require level 100** Salvage before they can be salvaged. Wooden, stone, leather, iron, and gold items have `MinimumLevel: 0`.
{.is-info}

| Field | Description |
|-------|-------------|
| `MinimumLevel` | Minimum Salvage skill level required to salvage this item. |
| `XpMultiplier` | Multiplier applied to base Salvage XP. |
| `MaximumQuantity` | Maximum number of `SalvageMaterial` that can be recovered. The actual quantity depends on durability — a full-durability item returns `MaximumQuantity`, a damaged item returns fewer. |
| `SalvageMaterial` | Bukkit `Material` name of the material to recover. |

---

## Default Salvageable Items

The file mirrors `repair.vanilla.yml` — every vanilla repairable item is also salvageable. Grouped by tier:

| Tier | Sample Items | Salvage Material |
|------|-------------|-----------------|
| Wood | Wooden tools | `OAK_PLANKS` |
| Stone | Stone tools | `COBBLESTONE` |
| Leather | Leather armour | `LEATHER` |
| Iron | Iron tools and armour | `IRON_INGOT` |
| Gold | Golden tools and armour | `GOLD_INGOT` |
| Diamond | Diamond tools and armour | `DIAMOND` |
| Netherite | Netherite tools and armour | `NETHERITE_INGOT` |

Bows, Crossbows, Fishing Rods, and Shields are also salvageable by default.

> Tridents and Elytra are **not** salvageable by default — add them manually if desired.
{.is-info}

---

## Tips

- **To cap the return quantity**, lower `MaximumQuantity`. A diamond sword at `MaximumQuantity: 1` can never return more than 1 diamond regardless of Arcane Salvage enchant recovery.
- **To require a skill level**, set `MinimumLevel`.
- **To add a custom item**, add a new entry under `Salvageables:` with all four fields.
- The material quantity is proportional to remaining durability. An item at 50% durability returns roughly half of `MaximumQuantity`.
