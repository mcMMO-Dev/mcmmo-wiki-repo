---
title: potions.yml
description: Alchemy Concoctions ingredient tiers and custom potion definition configuration reference.
published: true
date: 2026-07-12T00:00:00.000Z
tags: config, alchemy
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# potions.yml

`potions.yml` has two major responsibilities:

1. **Concoctions tier ingredient lists**: which brewing stand ingredients are unlocked at each Concoctions rank (Tiers 1–8).
2. **Potion definitions**: the full recipe graph used by Alchemy's custom brewing system (ingredients, resulting potions, effects, lore).

Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/potions.yml).

> This file is very large (≈1 900 lines). Most servers only need to edit the `Concoctions` section. Changes require a full server restart.
{.is-warning}

---

## Section 1: Concoctions Ingredients

The `Concoctions:` section defines which brewing ingredients a player can use at each Concoctions rank. A player can only use ingredients from tiers at or below their current rank.

```yaml
Concoctions:
    Tier_One_Ingredients:
        - NETHER_WART
        - GLOWSTONE_DUST
        # ...
    Tier_Two_Ingredients:
        - CARROT
        # ...
```

### Default Tier Assignments

| Tier | Unlocks At Rank | Default Ingredients |
|------|----------------|---------------------|
| Tier 1 | 1 | Breeze Rod, Blaze Powder, Fermented Spider Eye, Ghast Tear, Glowstone Dust, Golden Carrot, Magma Cream, Nether Wart, Redstone, Glistering Melon Slice, Spider Eye, Sugar, Gunpowder, Water Lily, Pufferfish, Dragon Breath, Stone, Slime Block, Cobweb, Turtle Helmet |
| Tier 2 | 2 | Carrot, Slime Ball, Phantom Membrane |
| Tier 3 | 3 | Quartz, Rabbit Foot |
| Tier 4 | 4 | Apple, Rotten Flesh |
| Tier 5 | 5 | Brown Mushroom, Ink Sac |
| Tier 6 | 6 | Fern |
| Tier 7 | 7 | Poisonous Potato |
| Tier 8 | 8 | Golden Apple |

> The rank at which each tier unlocks is configured in [`skillranks.yml`](/config/skillranks) under `Alchemy.Concoctions`.
{.is-info}

To add a new ingredient to a tier, add its Bukkit `Material` name to the appropriate `Tier_N_Ingredients` list:

```yaml
Tier_Three_Ingredients:
    - QUARTZ
    - RABBIT_FOOT
    - PRISMARINE_SHARD   # added custom ingredient
```

---

## Section 2: Potion Definitions

The `Potions:` section is a complete recipe graph. Each entry defines one potion variant: its material, base data, optional colour, optional lore, what ingredients transform it into other potions (`Children`), and what effects it applies.

```yaml
POTION_OF_HEALING:
    Material: POTION
    PotionData:
        PotionType: INSTANT_HEAL
    Children:
        FERMENTED_SPIDER_EYE: POTION_OF_HARMING
        GLOWSTONE_DUST: POTION_OF_HEALING_II
        GUNPOWDER: SPLASH_POTION_OF_HEALING
```

| Field | Description |
|-------|-------------|
| `Material` | Bukkit `Material`: `POTION`, `SPLASH_POTION`, `LINGERING_POTION`, or `TIPPED_ARROW`. |
| `PotionData.PotionType` | Vanilla Bukkit `PotionType` identifier (e.g. `HEALING`, `STRENGTH`, `WATER`). |
| `Color` | Optional RGB integer for the potion's colour in the bottle (e.g. `16711680` for red). |
| `Lore` | Optional list of strings to add as item lore. |
| `Children` | Map of `INGREDIENT_MATERIAL: RESULT_POTION_IDENTIFIER`. Defines what adding that ingredient in a brewing stand produces. |
| `Effects` | List of effect strings in the format `"<EFFECT_TYPE> <AMPLIFIER> <DURATION_TICKS>"`. |

### When to Edit the Potion Definitions

You typically **do not need to edit the `Potions:` section** unless you are:

- Adding entirely new custom potion types unique to your server.
- Changing which ingredients transform one potion into another (remapping the brewing graph).
- Adding custom lore or colours to existing potions.

The default definitions reproduce vanilla Minecraft's complete brewing tree plus custom Concoctions recipes.

> If you only want to control what ingredients players can use, edit the `Concoctions` tiers above, not the full potion graph.
{.is-info}

---

## Tips

- **To restrict the Concoctions skill entirely**, set all tier lists to empty (`[]`) or disable the sub-skill via [`coreskills.yml`](/config/coreskills).
- **To allow a specific ingredient earlier**, move it from a higher tier to a lower one.
- **To add a custom potion**, create a new entry in `Potions:` with a unique identifier, set `Material` and `PotionData`, then wire up `Children` paths from existing potions to reach it.
