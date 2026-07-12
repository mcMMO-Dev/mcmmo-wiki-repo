---
title: salvage.vanilla.yml
description: Vanilla item salvage configuration reference for mcMMO Salvage.
published: true
date: 2026-07-12T00:00:00.000Z
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

> For standard vanilla tools and armour mcMMO auto-detects the salvage material from the item's material tier (wood, stone, iron, diamond, and so on); no `SalvageMaterial` field is needed. Items that match no tier (e.g. Elytra) auto-detect to nothing, so you must specify `SalvageMaterial` explicitly for them.
{.is-info}

> By default, **diamond items require Salvage level 50** and **netherite items require Salvage level 100** before they can be salvaged. Wooden, stone, copper, leather, iron, and gold items have no level requirement.
{.is-info}

| Field | Description |
|-------|-------------|
| `MinimumLevel` | Minimum Salvage skill level required to salvage this item. |
| `XpMultiplier` | Multiplier applied to base Salvage XP. |
| `MaximumQuantity` | Maximum number of `SalvageMaterial` that can be recovered. The actual quantity depends on durability: a full-durability item returns `MaximumQuantity`, a damaged item returns fewer. |
| `SalvageMaterial` | Bukkit `Material` name of the material to recover. |

---

## Default Salvageable Items

The file covers most vanilla repairable items. The Shield, Mace, Elytra, and Warped Fungus on a Stick are notable exceptions: they are repairable but **not** salvageable by default. Grouped by tier:

| Tier | Sample Items | Salvage Material |
|------|-------------|-----------------|
| Wood | Wooden tools | `OAK_PLANKS` |
| Stone | Stone tools | `COBBLESTONE` |
| Copper | Copper tools and armour | `COPPER_INGOT` |
| Leather | Leather armour | `LEATHER` |
| Iron | Iron tools and armour | `IRON_INGOT` |
| Gold | Golden tools and armour | `GOLD_INGOT` |
| Diamond | Diamond tools and armour | `DIAMOND` |
| Netherite | Netherite tools and armour | `NETHERITE_SCRAP` |

Bows, Crossbows, Fishing Rods, Carrot on a Stick, Shears, and Flint and Steel are also salvageable by default.

> Elytra is **not** salvageable by default; add it manually as shown below. Trident **is** salvageable by default: its entry has no `SalvageMaterial`, so mcMMO auto-detects it as a Prismarine tool and returns Prismarine Crystals (up to 16 from a full-durability Trident).
{.is-info}

---

## Tips

- **To cap the return quantity**, lower `MaximumQuantity`. A diamond sword at `MaximumQuantity: 1` can never return more than 1 diamond; `MaximumQuantity` is the absolute ceiling regardless of other skill bonuses.
- **To require a skill level**, set `MinimumLevel`.
- **To add a custom item**, add a new entry under `Salvageables:` with all four fields.
- The material quantity is proportional to remaining durability. An item at 50% durability returns roughly half of `MaximumQuantity`.

---

## Examples

> `MinimumLevel` is compared directly against the player's Salvage level, using the same number in both Standard and Retro mode. `MinimumLevel: 75` requires Salvage level 75 either way.
{.is-info}

### Adding Elytra to salvage

Elytra is not salvageable by default. To allow it to yield Phantom Membranes (up to 8 from a full-durability Elytra):

```yaml
Salvageables:
    ELYTRA:
        MinimumLevel: 0
        XpMultiplier: 3
        MaximumQuantity: 8
        SalvageMaterial: PHANTOM_MEMBRANE
```

`SalvageMaterial` is required for items that match no material tier (like the Elytra). Without it mcMMO cannot determine what material to return.

### Adding Mace to salvage

Mace is not salvageable by default. To allow it to yield Breeze Rods:

```yaml
Salvageables:
    MACE:
        MinimumLevel: 0
        XpMultiplier: 3
        MaximumQuantity: 4
        SalvageMaterial: BREEZE_ROD
```

### Capping Diamond tool returns

By default a Diamond Sword returns up to 2 diamonds. To ensure no more than 1 is ever returned (even with high Arcane Salvage), lower `MaximumQuantity`:

```yaml
Salvageables:
    DIAMOND_SWORD:
        MinimumLevel: 50
        XpMultiplier: 0.5
        MaximumQuantity: 1
```

### Raising the level gate for Netherite salvage

Default Netherite items require Salvage level 100. To raise this to 150, set `MinimumLevel: 150`:

```yaml
Salvageables:
    NETHERITE_SWORD:
        MinimumLevel: 150
        XpMultiplier: 0.5
        MaximumQuantity: 4
```

Each Netherite item must be updated individually; there is no global override key.
