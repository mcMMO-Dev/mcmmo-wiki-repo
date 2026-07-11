---
title: skillranks.yml
description: Sub-skill rank unlock level configuration reference.
published: true
date: 2026-07-11T00:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# skillranks.yml

`skillranks.yml` defines the skill level required to unlock each rank of every sub-skill. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/skillranks.yml).

> Changes require a full server restart.
{.is-warning}

---

## Overview

Every sub-skill with multiple ranks has a block in this file with separate entries for **Standard** mode and **RetroMode**. RetroMode is cosmetically 10× higher; the underlying gameplay is identical.

```yaml
Fishing:
    TreasureHunter:
        Standard:
            Rank_1: 1
            Rank_2: 25
            Rank_3: 35
            ...
        RetroMode:
            Rank_1: 1
            Rank_2: 250
            Rank_3: 350
            ...
```

You **cannot** add or remove ranks via this file; the number of ranks per sub-skill is hardcoded. You can only change the level at which each rank unlocks.

Setting all ranks of a sub-skill to `0` gives all players the most powerful version immediately.

---

## Important Notes

- **Level requirements must be in ascending order** within a sub-skill. A rank cannot unlock at a lower level than the previous rank.
- Standard mode levels are in the range 0–100 by default. RetroMode levels are 0–1000 (10× Standard).
- The skill page for each skill lists the default rank unlock levels for its sub-skills. This file is the authoritative place to change them.

---

## Structure Reference

| Skill | Sub-Skills with configurable ranks |
|-------|------------------------------------|
| Acrobatics | Dodge (1 rank) |
| Alchemy | Catalysis (1 rank), Concoctions (8 ranks) |
| Archery | ArcheryLimitBreak (10 ranks), ArrowRetrieval (1), SkillShot (20) |
| Axes | AxesLimitBreak (10), SkullSplitter (1), CriticalStrikes (1), GreaterImpact (1), AxeMastery (4), ArmorImpact (20) |
| Crossbows | CrossbowsLimitBreak (10), PoweredShot (20), TrickShot (3) |
| Excavation | GigaDrillBreaker (1), Archaeology (8) |
| Fishing | Mastery (1), MagicHunter (1), IceFishing (1), Shake (8), MasterAngler (8), TreasureHunter (8), FishermansDiet (5) |
| Herbalism | DoubleDrops (1), VerdantBounty (1), GreenTerra (1), GreenThumb (4), FarmersDiet (5) |
| Maces | MacesLimitBreak (10), Cripple (4), Crush (4) |
| Mining | DoubleDrops (1), SuperBreaker (1), BiggerBombs (1), DemolitionsExpertise (1), MotherLode (1), BlastMining (8) |
| Repair | RepairMastery (1), SuperRepair (1), ArcaneForging (8) |
| Salvage | ScrapCollector (8), ArcaneSalvage (8) |
| Smelting | FuelEfficiency (3), UnderstandingTheArt (8) |
| Spears | SpearsLimitBreak (10), SpearMastery (8), Momentum (10) |
| Swords | SwordsLimitBreak (10), CounterAttack (1), SerratedStrikes (1), Stab (2), Rupture (4) |
| Taming | BeastLore (1), Gore (1), CallOfTheWild (1), Pummel (1), FastFoodService (1), EnvironmentallyAware (1), ThickFur (1), HolyHound (1), ShockProof (1), SharpenedClaws (1) |
| Tridents | TridentsLimitBreak (10), Impale (10) |
| Unarmed | UnarmedLimitBreak (10), Berserk (1), ArrowDeflect (1), Disarm (1), IronGrip (1), SteelArmStyle (20) |
| Woodcutting | TreeFeller (5), HarvestLumber (1), CleanCuts (1), KnockOnWood (2), LeafBlower (1) |

> **Smelting note:** `UnderstandingTheArt` is the internal YAML key for the Second Smelt sub-skill. `FuelEfficiency` has 3 ranks, not 8.
{.is-info}

> Sub-skills not listed above (such as Acrobatics Roll, Archery Daze, Herbalism HylianLuck) scale continuously by level and do not have rank unlock thresholds in this file. Their behaviour is tuned in [`advanced.yml`](/config/advanced).
{.is-info}

---

## Customisation Tips

**Grant a sub-skill from level 0:**
```yaml
Mining:
    BlastMining:
        Standard:
            Rank_1: 0
```

**Spread ranks more gradually:**
```yaml
Swords:
    Rupture:
        Standard:
            Rank_1: 10
            Rank_2: 30
            Rank_3: 60
            Rank_4: 90
```

**Disable a rank system entirely** (everyone gets max rank by setting all to 0):
```yaml
Archery:
    SkillShot:
        Standard:
            Rank_1: 0
            Rank_2: 0
            # ... all 20 ranks set to 0
```
