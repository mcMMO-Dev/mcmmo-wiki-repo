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

### Selected Default Entries

| Item | Drop Chance | Level Req (Standard) | Drops From |
|------|-------------|---------------------|------------|
| Glowstone Dust | 5.0% | 5 | Dirt, Sand, Grass, Mycelium |
| Gunpowder | 10.0% | 10 | Gravel |
| Bone | 10.0% | 20 | Gravel, Mud |
| Slime Ball | 5.0% | 15 | Clay |
| String | 5.0% | 25 | Clay |
| Cobweb | 5.0% | 75 | Clay |
| Egg | 1.0% | 25 | Grass Block |
| Red / Brown Mushroom | 0.5% | 50 | Dirt, Podzol, Grass, Mycelium, Mud |
| Cocoa Beans | 1.33% | 35 | Dirt, Grass, Mycelium, Mud |
| Diamond | 0.13% | 35 | Dirt, Sand, Gravel, Clay, Soul Sand |
| Music Disc 13 / Cat | 0.05% | 25 | All common dig blocks |
| Name Tag | 0.05% | 25 | All common dig blocks |
| Apple | 0.1% | 25 | Grass Block, Mycelium |
| Bucket | 0.1% | 50 | Clay |
| Clock | 0.1% | 50 | Clay |
| Spyglass | 0.1% | 7 | Mud, Dirt |
| Potato | 3.0% | 10 | Dirt, Mud |
| Stick | 2.0% | 1 | Mud, Muddy Mangrove Roots |
| Feather | 1.0% | 5 | Mud |
| Trident | 0.02% | 40 | Mud, Clay, Muddy Mangrove Roots |
| Soul Sand | 0.5% | 65 | Sand, Red Sand |
| Netherrack | 0.5% | 85 | Gravel |
| Quartz | 0.5% | 85 | Dirt, Sand, Gravel, Soul Sand |
| CAKE | 0.05% | 75 | All common dig blocks |
| Heart of the Sea | 0.01% | 90 | Mud |

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

## Adding Custom Treasures

To add a new treasure, add a new block under the appropriate section:

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

Valid material names are Bukkit `Material` enum names (see the [Spigot Javadocs](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html)). Names are case-insensitive.
