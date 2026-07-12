---
title: itemweights.yml
description: Item weight configuration for party equal-share mode.
published: true
date: 2026-07-12T00:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# itemweights.yml

`itemweights.yml` defines the relative value (weight) of items for use with party **equal item sharing**. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/itemweights.yml).

> Changes require a full server restart.
{.is-warning}

---

## How Equal Sharing Works

When a party uses the **EQUAL** item share mode, items that drop from mcMMO-triggered events (treasure, double drops, etc.) are distributed fairly among nearby party members. The weight of each item influences how the distribution is balanced: higher-weight items are considered more valuable and offset the value of other items received.

If an item is not listed, the `Default` weight (`5`) is used.

---

## Item_Weights

| Key | Default | Notes |
|-----|---------|-------|
| `Default` | `5` | Fallback weight for any item not listed. |
| `Diamond` / `Diamond_Ore` | `100` | |
| `Emerald` / `Emerald_Ore` | `150` | |
| `Quartz` / `Nether_Quartz_Ore` | `200` | |
| `Gold_Ingot` / `Gold_Ore` | `50` | |
| `Iron_Ingot` / `Iron_Ore` | `40` | |
| `Lapis_Ore` / `Redstone` / `Redstone_Ore` | `30` | |
| `Glowstone_Dust` | `20` | |
| `Coal` / `Coal_Ore` | `10` | |
| Diamond tools and armour | `150` | |
| Golden tools and armour | `75` | |
| Iron tools and armour | `60` | |

Item weight keys use the title-case form of the Bukkit `Material` name: each word is capitalised and the words are joined with underscores, so `DIAMOND_SWORD` becomes `Diamond_Sword`. These keys are case-sensitive and must match that exact form.

---

## Party_Shareables

The `Party_Shareables.Misc_Items` list defines which items are eligible to be shared via the **Misc** share category. By default this includes a broad set of weapons and armour. You can add or remove items using their `Material` name. Entries here are matched case-insensitively, so `Diamond_Sword`, `DIAMOND_SWORD`, and `diamond_sword` all resolve to the same item.

```yaml
Party_Shareables:
    Misc_Items:
        - Diamond_Sword
        - Iron_Pickaxe
        # Add any material name here
```
