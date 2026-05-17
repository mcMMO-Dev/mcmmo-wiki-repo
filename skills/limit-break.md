---
title: Limit Break
description: "Information about the Limit Break mechanic shared across mcMMO combat skills."
published: true
date: 2024-11-24T01:41:45.231Z
tags: skills, combat, limit-break
editor: markdown
dateCreated: 2024-11-24T01:41:45.231Z
---

# Limit Break

Limit Break is a passive sub-skill available to several mcMMO combat skills. It adds bonus damage on top of a hit, with the bonus scaling based on the quality of the defender's armour. Higher-ranked Limit Break deals more damage, but the full damage is only realised against heavily armoured targets — lighter armour receives less of the bonus.

## Skills with Limit Break

| Skill | Sub-skill name |
|-------|----------------|
| Archery | Archery Limit Break |
| Axes | Axes Limit Break |
| Crossbows | Crossbows Limit Break |
| Maces | Maces Limit Break |
| Spears | Spears Limit Break |
| Swords | Swords Limit Break |
| Tridents | Tridents Limit Break |
| Unarmed | Unarmed Limit Break |

## Damage Formula

The raw bonus damage equals the player's current Limit Break **rank** (a whole number, 1–10). That number is then multiplied by an armour-quality modifier based on the total armour quality score of the defender:

$$\text{bonus} = \lfloor \text{rank} \times \text{armourModifier} \rfloor$$

| Defender armour quality score | Modifier | Effective bonus at rank 10 |
|-------------------------------|----------|---------------------------|
| 0 – 4 | ×0.25 | 2 HP |
| 5 – 8 | ×0.50 | 5 HP |
| 9 – 12 | ×0.75 | 7 HP |
| > 12 | ×1.00 | 10 HP |

Against **mobs** (when PvE is enabled), the quality score is treated as 1000, so the full ×1.00 modifier always applies.

## Armour Quality Scores

Each worn armour piece contributes a fixed number of points to the defender's total armour quality score:

| Armour material | Points per piece | Full set total |
|----------------|-----------------|----------------|
| Leather | 1 | 4 |
| Copper | 1 | 4 |
| Iron | 2 | 8 |
| Gold | 3 | 12 |
| Chainmail | 3 | 12 |
| Diamond | 6 | 24 |
| Netherite | 12 | 48 |

A player wearing a full iron set (score 8) falls in the 5–8 bracket (×0.50 modifier). A player wearing a mix of diamond and netherite can easily exceed 12 and always receive the full bonus.

## PvP vs PvE

By default, Limit Break only activates in **PvP** (attacks on other players). It does not apply to mobs unless explicitly enabled in `advanced.yml`:

```yml
Skills:
    General:
        LimitBreak:
            AllowPVE: false
```

Setting `AllowPVE: true` enables Limit Break against mobs. Against mobs, the armour quality check is bypassed and the full rank bonus is always applied.

## Rank Unlock Levels

All Limit Break sub-skills share the same 10-rank progression with identical unlock levels:

| Rank | Unlock level |
|------|-------------|
| 1 | 100 |
| 2 | 200 |
| 3 | 300 |
| 4 | 400 |
| 5 | 500 |
| 6 | 600 |
| 7 | 700 |
| 8 | 800 |
| 9 | 900 |
| 10 | 1000 |
