---
title: advanced.yml
description: Advanced per-skill tuning configuration reference.
published: true
date: 2026-05-17T00:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# advanced.yml

`advanced.yml` exposes the numeric tuning knobs for almost every mcMMO sub-skill — chance caps, damage modifiers, bonus levels, and more. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/advanced.yml).

> This file is intended for advanced users. Most servers will not need to change anything here. Changes require a full server restart.
{.is-warning}

> Sub-skill rank unlock levels are **not** in this file — those are in [`skillranks.yml`](/config/skillranks).
{.is-info}

---

## Metrics / Feedback

| Key | Default | Description |
|-----|---------|-------------|
| `Metrics.bstats` | `true` | Send anonymous usage stats to bStats. |
| `Feedback.PlayerTips` | `true` | Show contextual tips to players (e.g. how to use a new sub-skill). |
| `Feedback.SkillCommand.BlankLinesAboveHeader` | `true` | Add spacing above skill command headers in chat. |
| `Feedback.Events.XP.SendTitles` | `true` | Show XP gain notifications as large title text on screen in addition to the action bar. Set to `false` for a less intrusive HUD. |
| `Feedback.Events.AbilityActivation.SendNotificationToOtherPlayers` | `true` | Broadcast a message to nearby players when someone activates a super-ability. |

### Action Bar Notifications

The `Feedback.ActionBarNotifications` block controls which mcMMO messages appear on the action bar (the line just above the hotbar) versus being sent to chat. Each entry has:

| Sub-key | Description |
|---------|-------------|
| `Enabled` | Show this notification in the action bar. |
| `SendCopyOfMessageToChat` | Also send the message to chat when shown on the action bar. |

Selected entries (many more exist in the file):

| Key | Default Enabled |
|-----|----------------|
| `AbilityOff` | `true` |
| `AbilityCoolDown` | `true` |
| `LevelUps` | `true` (also copies to chat) |
| `SubSkillUnlocked` | `true` |
| `ExperienceGain` | `true` |
| `SubSkillFailed` | `false` |

---

## General Skill Settings

| Key | Default | Description |
|-----|---------|-------------|
| `Skills.General.Attack_Cooldown.Adjust_Skills_For_Attack_Cooldown` | `true` | Scale proc chances down for rapid attacks (full-strength hit = full chance). |
| `Skills.General.LimitBreak.AllowPVE` | `false` | Allow Limit Break bonuses to apply in PvE (mobs). By default Limit Break only affects PvP. |
| `Skills.General.StartingLevel` | `0` | Level every new player starts at in all skills. |

### Ability Length

Ability duration (in seconds) scales with player level:

| Key | Default |
|-----|---------|
| `Ability.Length.Standard.CapLevel` | `100` |
| `Ability.Length.Standard.IncreaseLevel` | `5` |
| `Ability.Length.RetroMode.CapLevel` | `1000` |
| `Ability.Length.RetroMode.IncreaseLevel` | `50` |
| `Ability.EnchantBuff` | `5` |

**How it works:** The ability gains 1 second of duration for every `IncreaseLevel` skill levels up to `CapLevel`. `EnchantBuff` sets the enchantment level used when buffing Super Breaker and Giga Drill Breaker (instead of potion buffs, if `hidden.yml` sets `EnchantmentBuffs: true`).

---

## Acrobatics

| Key | Default | Description |
|-----|---------|-------------|
| `Dodge.ChanceMax` | `20.0` | Maximum chance (%) to dodge at `MaxBonusLevel`. |
| `Dodge.MaxBonusLevel.Standard` | `100` | Level where dodge chance reaches `ChanceMax`. |
| `Dodge.DamageModifier` | `2.0` | Dodged damage is divided by this value (dodge halves damage at default). |
| `Roll.ChanceMax` | `100.0` | Maximum roll chance (%). |
| `Roll.MaxBonusLevel.Standard` | `100` | Level where roll chance reaches `ChanceMax`. |
| `Roll.DamageThreshold` | `7.0` | Maximum fall damage (in half-hearts) a normal Roll can negate. |
| `GracefulRoll.DamageThreshold` | `14.0` | Same but for a Graceful Roll (sneaking while falling). |

---

## Alchemy

| Key | Default | Description |
|-----|---------|-------------|
| `Catalysis.MaxBonusLevel.Standard` | `100` | Level where brewing speed reaches `MaxSpeed`. |
| `Catalysis.MinSpeed` | `1.0` | Brewing speed multiplier at the lowest rank (1× = vanilla speed). |
| `Catalysis.MaxSpeed` | `4.0` | Brewing speed multiplier at `MaxBonusLevel`. |

---

## Archery

| Key | Default | Description |
|-----|---------|-------------|
| `SkillShot.RankDamageMultiplier` | `10.0` | Each rank adds this percentage of bonus arrow damage. Rank 8 = +80% at default. |
| `SkillShot.MaxDamage` | `9.0` | Absolute cap on Skill Shot bonus damage (in half-hearts). |
| `Daze.ChanceMax` | `50.0` | Maximum Daze proc chance (%). |
| `Daze.MaxBonusLevel.Standard` | `100` | Level where Daze reaches `ChanceMax`. |
| `Daze.BonusDamage` | `4.0` | Extra damage dealt when a Daze procs (in half-hearts). |
| `ArrowRetrieval.ChanceMax` | `100.0` | Maximum chance to retrieve arrows from mobs (%). |
| `ForceMultiplier` | `2.0` | Archery XP is multiplied by this when a fully-charged shot is fired. |

---

## Crossbows

| Key | Default | Description |
|-----|---------|-------------|
| `PoweredShot.RankDamageMultiplier` | `10.0` | Bonus damage per rank as a percentage (mirrors Archery's Skill Shot). |
| `PoweredShot.MaxDamage` | `9.0` | Cap on PoweredShot bonus damage. |

---

## Axes

| Key | Default | Description |
|-----|---------|-------------|
| `AxeMastery.RankDamageMultiplier` | `1.0` | Flat damage added per rank (rank 4 = +4.0 hearts). |
| `CriticalStrikes.ChanceMax` | `37.5` | Maximum critical hit chance (%). |
| `CriticalStrikes.PVP_Modifier` | `1.5` | Damage multiplier for critical hits in PvP. |
| `CriticalStrikes.PVE_Modifier` | `2.0` | Damage multiplier for critical hits in PvE. |
| `GreaterImpact.Chance` | `25.0` | Chance to trigger Greater Impact (knockback + bonus damage). |
| `GreaterImpact.KnockbackModifier` | `1.5` | Velocity multiplier for knockback. |
| `GreaterImpact.BonusDamage` | `2.0` | Extra damage when Greater Impact procs. |
| `ArmorImpact.DamagePerRank` | `6.5` | Durability damage dealt to target armour per rank per hit. |
| `ArmorImpact.Chance` | `25.0` | Chance to trigger Armor Impact. |
| `SkullSplitter.DamageModifier` | `2.0` | AoE splash damage is divided by this modifier. |

---

## Fishing

| Key | Default | Description |
|-----|---------|-------------|
| `ShakeChance.Rank_1–8` | `15–75%` | Per-rank proc chance for Shake. |
| `VanillaXPMultiplier.Rank_1–8` | `1–5×` | Per-rank multiplier on vanilla XP orbs from fishing. |
| `FishermansDiet.RankChange` | `20` | Every `RankChange` Fishing levels, Fisherman's Diet gains a rank. |

### Master Angler

| Key | Default | Description |
|-----|---------|-------------|
| `MasterAngler.Tick_Reduction_Per_Rank.Min_Wait` | `10` | Min-wait tick reduction per rank. |
| `MasterAngler.Tick_Reduction_Per_Rank.Max_Wait` | `30` | Max-wait tick reduction per rank. |
| `MasterAngler.Boat_Tick_Reduction.Min_Wait` | `10` | Additional min-wait reduction when in a boat. |
| `MasterAngler.Boat_Tick_Reduction.Max_Wait` | `30` | Additional max-wait reduction when in a boat. |
| `MasterAngler.Tick_Reduction_Caps.Min_Wait` | `40` | Floor for the minimum wait (ticks). Do not change without fully understanding the fishing timer. |
| `MasterAngler.Tick_Reduction_Caps.Max_Wait` | `100` | Floor for the maximum wait (ticks). |

---

## Herbalism

| Key | Default | Description |
|-----|---------|-------------|
| `GreenThumb.ChanceMax` | `100.0` | Maximum Green Thumb chance (%). |
| `GreenThumb.MaxBonusLevel.Standard` | `100` | Level where Green Thumb reaches `ChanceMax`. |
| `DoubleDrops.ChanceMax` | `100.0` | Maximum double drop chance for Herbalism. |
| `HylianLuck.ChanceMax` | `10.0` | Maximum Hylian Luck proc chance (%). |
| `HylianLuck.MaxBonusLevel.Standard` | `100` | Level where Hylian Luck reaches `ChanceMax`. |
| `ShroomThumb.ChanceMax` | `50.0` | Maximum Shroom Thumb chance (%). |
| `VerdantBounty.ChanceMax` | `50.0` | Maximum Verdant Bounty (triple drop) chance (%). |
| `VerdantBounty.MaxBonusLevel.Standard` | `1000` | Level where Verdant Bounty reaches its cap. |

---

## Mining

| Key | Default | Description |
|-----|---------|-------------|
| `DoubleDrops.ChanceMax` | `100.0` | Maximum Mining double drop chance (%). |
| `DoubleDrops.SilkTouch` | `true` | Allow double drops to proc when mining with a Silk Touch tool. Set to `false` to disable double drops for Silk Touch. |
| `SuperBreaker.AllowTripleDrops` | `true` | Allow Super Breaker to produce triple drops. |
| `MotherLode.ChanceMax` | `50.0` | Maximum chance to proc Mother Lode (extra ore drops without Super Breaker). |
| `MotherLode.MaxBonusLevel.Standard` | `1000` | Level where Mother Lode reaches its cap. |

### Blast Mining

Blast Mining procs when you detonate TNT while crouching. These values tune each rank's bonuses:

| Key | Default | Description |
|-----|---------|-------------|
| `Bonus_Drops.Enabled` | `true` | Master toggle for all blast mining bonus drops. Set to `false` to disable ore bonuses, debris reduction, and drop multipliers from blast mining entirely. |
| `BlastDamageDecrease.Rank_1–8` | — | % of TNT explosion damage negated (0 / 0 / 0 / 25 / 25 / 50 / 50 / 100). |
| `OreBonus.Rank_1–8` | — | % extra ores received (35 / 40 / 45 / 50 / 55 / 60 / 65 / 70). |
| `DebrisReduction.Rank_1–8` | — | % fewer non-ore drops (10 / 20 / 30 / 30 / 30 / 30 / 30 / 30). |
| `DropMultiplier.Rank_1–8` | — | Times each ore drops (1 / 1 / 1 / 1 / 2 / 2 / 3 / 3). |
| `BlastRadiusModifier.Rank_1–8` | — | Extra blast radius added (1 / 1 / 2 / 2 / 3 / 3 / 4 / 4). |

---

## Repair

| Key | Default | Description |
|-----|---------|-------------|
| `RepairMastery.MaxBonusPercentage` | `200.0` | Maximum bonus durability restored (%) on top of base repair. |
| `RepairMastery.MaxBonusLevel.Standard` | `100` | Level where Repair Mastery reaches its cap. |
| `SuperRepair.ChanceMax` | `100.0` | Maximum Super Repair chance (%). |
| `ArcaneForging.May_Lose_Enchants` | `true` | Enchants can be lost when repairing enchanted items. |
| `ArcaneForging.MaxEnchantLevel` | `5` | Maximum enchant level Arcane Forging will keep or downgrade to. |
| `ArcaneForging.Keep_Enchants_Chance.Rank_1–8` | `10–60%` | Per-rank chance to keep an enchant fully intact. |
| `ArcaneForging.Downgrades_Enabled` | `true` | Enchants can be downgraded (one level lower) instead of fully lost. |
| `ArcaneForging.Downgrades_Chance.Rank_1–8` | `75–10%` | Per-rank chance that a kept enchant is downgraded instead of preserved. |

---

## Salvage

| Key | Default | Description |
|-----|---------|-------------|
| `ArcaneSalvage.EnchantLossEnabled` | `true` | Enchants can be lost when salvaging. |
| `ArcaneSalvage.EnchantDowngradeEnabled` | `true` | Enchants can be downgraded when salvaging. |
| `ArcaneSalvage.MaxEnchantLevel` | `5` | Maximum enchant level Arcane Salvage will preserve. |
| `ArcaneSalvage.ExtractFullEnchant.Rank_1–8` | `2.5–32.5%` | Per-rank chance to extract the full enchant onto a book. |
| `ArcaneSalvage.ExtractPartialEnchant.Rank_1–8` | `2.0–17.5%` | Per-rank chance to extract a downgraded enchant onto a book. |

---

## Smelting

| Key | Default | Description |
|-----|---------|-------------|
| `SecondSmelt.ChanceMax` | `50.0` | Maximum chance to get a second smelted item (%). |
| `SecondSmelt.MaxBonusLevel.Standard` | `100` | Level where Second Smelt reaches `ChanceMax`. |
| `VanillaXPMultiplier.Rank_1–8` | `1–5×` | Per-rank multiplier on vanilla furnace XP orbs. |

> `FluxMining` (mine ores to get smelted output directly) is configured here but its settings have no practical effect — it was removed from gameplay.
{.is-warning}

---

## Swords

| Key | Default | Description |
|-----|---------|-------------|
| `Stab.Base_Damage` | `1.0` | Base damage bonus for Stab (in half-hearts). |
| `Stab.Per_Rank_Multiplier` | `1.5` | Damage multiplier added per rank. |
| `CounterAttack.ChanceMax` | `30.0` | Maximum Counter Attack chance (%). |
| `CounterAttack.DamageModifier` | `2.0` | Incoming damage is divided by this modifier and reflected back. |
| `SerratedStrikes.DamageModifier` | `4.0` | AoE splash damage modifier for Serrated Strikes. |
| `SerratedStrikes.BleedTicks` | `5` | Bleed duration (in ticks) applied by Serrated Strikes. |

### Rupture

Rupture applies a damage-over-time effect. Each rank has independent settings for PvP and PvE:

| Key | Description |
|-----|-------------|
| `Rupture.Chance_To_Apply_On_Hit.Rank_1–4` | Proc chance (15 / 33 / 40 / 66 %). |
| `Rupture.Duration_In_Seconds` | How long Rupture lasts (default 5 s for both PvP and PvE). |
| `Rupture.Tick_Interval_Damage` | Damage per tick (pure damage, ignores armour). Different per PvP and PvE. |
| `Rupture.Explosion_Damage` | Damage if Rupture expires without being refreshed (reduced by armour). |

---

## Taming

| Key | Default | Description |
|-----|---------|-------------|
| `Gore.ChanceMax` | `100.0` | Maximum Gore proc chance (%). |
| `Gore.Modifier` | `2.0` | Damage multiplier when Gore activates. |
| `FastFoodService.Chance` | `50.0` | Chance for a wolf to heal when it deals damage. |
| `ThickFur.Modifier` | `2.0` | Damage taken by pets is divided by this. |
| `ShockProof.Modifier` | `6.0` | Explosion damage taken by pets is divided by this. |
| `SharpenedClaws.Bonus` | `2.0` | Extra damage (half-hearts) added to pet attacks. |
| `CallOfTheWild.MinHorseJumpStrength` | `0.7` | Minimum jump strength of summoned horses. |
| `CallOfTheWild.MaxHorseJumpStrength` | `2.0` | Maximum jump strength of summoned horses. |
| `Pummel.Chance` | `10.0` | Chance for a pet to pummel (stun) a target. |

---

## Unarmed

| Key | Default | Description |
|-----|---------|-------------|
| `Disarm.ChanceMax` | `33.0` | Maximum Disarm proc chance (%). |
| `Disarm.AntiTheft` | `false` | Only the disarmed player can pick up their dropped item. |
| `ArrowDeflect.ChanceMax` | `50.0` | Maximum arrow deflection chance (%). |
| `IronGrip.ChanceMax` | `100.0` | Maximum chance to resist being disarmed. |
| `SteelArmStyle.Damage_Override` | `false` | Use the override table instead of the vanilla unarmed damage formula. |
| `SteelArmStyle.Override.Rank_1–20` | `1.0–13.5` | Damage values per rank when `Damage_Override` is `true`. |

---

## Woodcutting

| Key | Default | Description |
|-----|---------|-------------|
| `TreeFeller.Knock_On_Wood.Add_XP_Orbs_To_Drops` | `true` | Drop vanilla XP orbs from Tree Feller. |
| `CleanCuts.ChanceMax` | `50.0` | Maximum triple-drop chance (%). |
| `CleanCuts.MaxBonusLevel.Standard` | `1000` | Level where CleanCuts reaches `ChanceMax`. |
| `HarvestLumber.ChanceMax` | `100.0` | Maximum double-drop chance (%). |
| `HarvestLumber.MaxBonusLevel.Standard` | `100` | Level where HarvestLumber reaches `ChanceMax`. |

---

## Maces

| Key | Default | Description |
|-----|---------|-------------|
| `Maces.Crush.Base_Damage` | `0.5` | Flat damage bonus applied at rank 1. |
| `Maces.Crush.Rank_Damage_Multiplier` | `1.0` | Additional damage per rank beyond rank 1. |
