---
title: treasures.yml
description: Excavation Archaeology and Hylian Luck treasure drop configuration reference.
published: true
date: 2026-05-17T00:00:00.000Z
tags: config, excavation, herbalism
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# treasures.yml

`treasures.yml` configures the treasure tables for two Herbalism and Excavation sub-skills:

- **Archaeology** (Excavation) — items found while digging dirt, sand, gravel, clay, and similar blocks
- **Hylian Luck** (Herbalism) — items found by breaking bushes, flowers, and flower pots

Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/treasures.yml).

> Changes require a full server restart.
{.is-warning}

---

## Entry Format

Both sections share the same field structure:

```yaml
<MATERIAL_NAME>:
    Amount: 1
    XP: 100
    Drop_Chance: 5.0
    Level_Requirement:
        Standard_Mode: 25
        Retro_Mode: 250
    Drops_From: [Dirt, Gravel, Sand]
```

| Field | Description |
|-------|-------------|
| `Amount` | Number of the item given per successful drop. |
| `XP` | Bonus Excavation/Herbalism XP awarded when this item drops. |
| `Drop_Chance` | Percentage chance (0–100) that this item drops when the block is broken and the sub-skill procs. This is evaluated independently for each entry, so multiple items can drop from one block. |
| `Level_Requirement.Standard_Mode` | Minimum skill level (Standard mode) required for this item to be eligible. |
| `Level_Requirement.Retro_Mode` | Minimum skill level (Retro mode, 10× scale). |
| `Drops_From` | List of block `Material` names this item can drop from. Only blocks in this list will yield the drop. |

---

## Excavation: Archaeology Drops

The `Excavation:` section lists items that can be found by the Archaeology sub-skill. The items are drawn from a wide range of blocks including dirt, grass, sand, gravel, clay, soul sand, mycelium, mud, and muddy mangrove roots.

### Block Groups

Several entries share a large common block list. The shorthand labels used in the table below refer to these exact block sets.

> These groups reflect the **default** configuration. Any entry's `Drops_From` list can be freely changed — these names are just a reading convenience for this page.
{.is-info}

| Label | Blocks |
|-------|--------|
| All dig blocks | Dirt, Coarse Dirt, Podzol, Grass Block, Sand, Red Sand, Gravel, Clay, Mycelium, Soul Sand, Soul Soil, Mud |
| Dig blocks (no Mud) | Dirt, Coarse Dirt, Podzol, Grass Block, Sand, Red Sand, Gravel, Clay, Mycelium, Soul Sand, Soul Soil |
| Dig blocks (no Clay or Mud) | Dirt, Coarse Dirt, Podzol, Grass Block, Sand, Red Sand, Gravel, Mycelium, Soul Sand, Soul Soil |
| Dirt variants, sand, and mycelium | Dirt, Coarse Dirt, Podzol, Grass Block, Sand, Red Sand, Mycelium |
| Soil and mud | Dirt, Coarse Dirt, Podzol, Grass Block, Mycelium, Mud |

### Selected Default Entries

| Item | Drop Chance | Level Req (Retro) | Drops From |
|------|-------------|------------------|------------|
| Glowstone Dust | 5.0% | 50 | Dirt variants, sand, and mycelium |
| Gunpowder | 10.0% | 100 | Gravel |
| Bone | 10.0% | 200 | Gravel, Mud |
| Slime Ball | 5.0% | 150 | Clay |
| String | 5.0% | 250 | Clay |
| Cobweb | 5.0% | 750 | Clay |
| Egg | 1.0% | 250 | Grass Block |
| Red / Brown Mushroom | 0.5% | 500 | Soil and mud |
| Cocoa Beans | 1.33% | 350 | Soil and mud |
| Diamond | 0.13% | 350 | All dig blocks |
| Music Disc 13 / Cat | 0.05% | 250 | Dig blocks (no Mud) |
| Name Tag | 0.05% | 250 | Dig blocks (no Mud) |
| Apple | 0.1% | 250 | Grass Block, Mycelium |
| Bucket | 0.1% | 500 | Clay |
| Clock | 0.1% | 500 | Clay |
| Spyglass | 0.1% | 70 | Mud, Dirt |
| Potato | 3.0% | 100 | Dirt, Mud |
| Stick | 2.0% | 10 | Mud, Muddy Mangrove Roots |
| Feather | 1.0% | 50 | Mud |
| Trident | 0.02% | 400 | Mud, Clay, Muddy Mangrove Roots |
| Soul Sand | 0.5% | 650 | Sand, Red Sand |
| Netherrack | 0.5% | 850 | Gravel |
| Quartz | 0.5% | 850 | Dig blocks (no Clay or Mud) |
| Cake | 0.05% | 750 | Dig blocks (no Mud) |
| Heart of the Sea | 0.01% | 900 | Mud |

> The `Drop_Chance` is evaluated per item entry, so at high levels a single block break can drop multiple different items simultaneously.
{.is-info}

---

## Hylian Luck Drops

The `Hylian_Luck:` section lists items that can drop from breaking naturally occurring bushes, flowers, and flower pots. In Retro Mode, `Level_Requirement` is multiplied by 10.

The `Drops_From` field uses special category names rather than individual block names:

| Category | Blocks Included |
|----------|----------------|
| `Bushes` | Various shrubs and small plants |
| `Flowers` | All flower types |
| `Pots` | Flower pots |

### Default Drops

| Item | Drop Chance | Level Req | From |
|------|-------------|-----------|------|
| Melon Seeds | 100% | 0 | Bushes |
| Pumpkin Seeds | 100% | 0 | Bushes |
| Cocoa Beans | 100% | 0 | Bushes |
| Carrot | 100% | 0 | Flowers |
| Potato | 100% | 0 | Flowers |
| Apple | 100% | 0 | Flowers |
| Emerald | 100% | 0 | Pots |
| Diamond | 100% | 0 | Pots |
| Gold Nugget | 100% | 0 | Pots |
| Copper Nugget | 100% | 0 | Pots |

> A 100% `Drop_Chance` here does not mean these always drop — the Hylian Luck sub-skill itself has its own proc chance controlled by `advanced.yml`. These values only govern the distribution once the proc fires.
{.is-warning}

---

## Examples

Valid material names for all entries are Bukkit `Material` enum names (see the [Spigot Javadocs](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html)). Names are case-insensitive.

> The full entry must be present. mcMMO loads each material key completely from the file — you cannot partially override a single field.
{.is-info}

### Adding a new Excavation drop

To add Emeralds as a rare find from dirt and gravel, unlocked at level 400 (Retro):

```yaml
Excavation:
    EMERALD:
        Amount: 1
        XP: 500
        Drop_Chance: 0.5
        Level_Requirement:
            Standard_Mode: 40
            Retro_Mode: 400
        Drops_From: [Dirt, Gravel, Sand, Clay]
```

### Making an existing Excavation item rarer

The default Diamond has a `Drop_Chance` of 0.13. To tighten that to 0.05%:

```yaml
Excavation:
    DIAMOND:
        Amount: 1
        XP: 1000
        Drop_Chance: 0.05
        Level_Requirement:
            Standard_Mode: 35
            Retro_Mode: 350
        Drops_From: [Dirt, Coarse_Dirt, Podzol, Grass_Block, Sand, Red_Sand, Gravel, Clay, Mycelium, Soul_Sand, Soul_Soil, Mud]
```

### Restricting an item to fewer block types

To limit Diamond drops to Clay only, change the `Drops_From` line:

```yaml
        Drops_From: [Clay]
```

Use the same list format when expanding an item to more blocks — e.g. `[Dirt, Sand, Gravel, Clay, Soul_Sand, Mud]`.

### Adding a Hylian Luck drop

To add a small chance to find a Totem of Undying when breaking flower pots:

```yaml
Hylian_Luck:
    TOTEM_OF_UNDYING:
        Amount: 1
        XP: 5000
        Drop_Chance: 0.01
        Level_Requirement:
            Standard_Mode: 0
            Retro_Mode: 0
        Drops_From: [Pots]
```

> The `Drop_Chance` here interacts with the Hylian Luck proc chance configured in `advanced.yml` (`HylianLuck.ChanceMax`, default `10.0%` at max level). A 0.01% `Drop_Chance` combined with a 10% proc chance means the effective per-break chance at max level is roughly 0.001%.
{.is-info}

### Raising XP for a high-value find

To make finding a Heart of the Sea also award bonus Excavation XP, increase its `XP` value (default is 9999 — the highest in the file):

```yaml
Excavation:
    HEART_OF_THE_SEA:
        Amount: 1
        XP: 50000
        Drop_Chance: 0.01
        Level_Requirement:
            Standard_Mode: 90
            Retro_Mode: 900
        Drops_From: [Mud]
```
