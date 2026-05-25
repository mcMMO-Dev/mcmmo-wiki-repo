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

> By default, **diamond items require level 500** and **netherite items require level 1000** Salvage (Retro) before they can be salvaged. Wooden, stone, leather, iron, and gold items have no level requirement.
{.is-info}

| Field | Description |
|-------|-------------|
| `MinimumLevel` | Minimum Salvage skill level required to salvage this item. |
| `XpMultiplier` | Multiplier applied to base Salvage XP. |
| `MaximumQuantity` | Maximum number of `SalvageMaterial` that can be recovered. The actual quantity depends on durability — a full-durability item returns `MaximumQuantity`, a damaged item returns fewer. |
| `SalvageMaterial` | Bukkit `Material` name of the material to recover. |

---

## Default Salvageable Items

The file covers most vanilla repairable items. The Shield, Mace, Elytra, and Warped Fungus on a Stick are notable exceptions — they are repairable but **not** salvageable by default. Grouped by tier:

| Tier | Sample Items | Salvage Material |
|------|-------------|-----------------|
| Wood | Wooden tools | `OAK_PLANKS` |
| Stone | Stone tools | `COBBLESTONE` |
| Leather | Leather armour | `LEATHER` |
| Iron | Iron tools and armour | `IRON_INGOT` |
| Gold | Golden tools and armour | `GOLD_INGOT` |
| Diamond | Diamond tools and armour | `DIAMOND` |
| Netherite | Netherite tools and armour | `NETHERITE_INGOT` |

Bows, Crossbows, and Fishing Rods are also salvageable by default.

> Elytra is **not** salvageable by default — add it manually as shown below. Trident has an entry but no `SalvageMaterial` and no crafting recipe, so it yields nothing; add `SalvageMaterial` and `MaximumQuantity` to the existing Trident entry to enable salvage.
{.is-info}

---

## Tips

- **To cap the return quantity**, lower `MaximumQuantity`. A diamond sword at `MaximumQuantity: 1` can never return more than 1 diamond — `MaximumQuantity` is the absolute ceiling regardless of other skill bonuses.
- **To require a skill level**, set `MinimumLevel`.
- **To add a custom item**, add a new entry under `Salvageables:` with all four fields.
- The material quantity is proportional to remaining durability. An item at 50% durability returns roughly half of `MaximumQuantity`.

---

## Examples

> `MinimumLevel` is always specified in **Standard mode** units regardless of your server's level mode. Retro mode players see 10× this value in-game (e.g. `MinimumLevel: 75` = level 750 in Retro mode).
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

`SalvageMaterial` is required for items with no crafting recipe. Without it mcMMO cannot determine what material to return.

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

By default a Diamond Sword returns up to 2 diamonds. To ensure no more than 1 is ever returned — even with high Arcane Salvage — lower `MaximumQuantity`:

```yaml
Salvageables:
    DIAMOND_SWORD:
        MinimumLevel: 50
        XpMultiplier: 0.5
        MaximumQuantity: 1
```

### Raising the level gate for Netherite salvage

Default Netherite items require Salvage level 1000 (Retro). To raise this to 1500 (Retro), set `MinimumLevel: 150`:

```yaml
Salvageables:
    NETHERITE_SWORD:
        MinimumLevel: 150
        XpMultiplier: 0.5
        MaximumQuantity: 4
```

Each Netherite item must be updated individually — there is no global override key.
