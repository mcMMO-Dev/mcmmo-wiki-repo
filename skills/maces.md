---
title: Maces
description: "Information about the Maces skill."
published: true
date: 2024-11-24T01:39:37.779Z
tags: maces, skills
editor: markdown
dateCreated: 2024-04-13T18:16:00.881Z
---

# Maces

> Maces is a newer skill that is still being expanded. Some features and balance may change in future releases. Join the [mcMMO Discord](https://discord.gg/mcmmo) for the latest news.
{.is-warning}

The Maces skill governs combat with maces. XP is earned by striking mobs or players with a mace. Levelling Maces unlocks passive damage bonuses, a slowness-on-hit effect, and a PvP damage multiplier.

## At a glance

| | |
|---|---|
| **Category** | Combat (melee) |
| **Primary tool** | Mace |
| **Super ability** | None |
| **Parent skill(s)** | None |
| **Child skill(s)** | None |

## XP Gain

XP is granted each time a mace strike lands on a mob or player. The amount is determined by the target's entity type, following the same combat XP table used by other weapon skills.

## Sub-Skills

### Crush

**Ranks:** 4

Crush is a passive sub-skill that adds a flat damage bonus to every mace hit. The bonus scales with rank.

| Rank | Unlock level | Bonus damage (HP) |
|------|-------------|-------------------|
| 1    | 100         | 1.5               |
| 2    | 250         | 2.5               |
| 3    | 750         | 3.5               |
| 4    | 900         | 4.5               |

**Formula:** `bonus = Base_Damage + (rank x Rank_Damage_Multiplier)`

**Config keys** (`advanced.yml` under `Skills.Maces.Crush`):

| Key | Default | Description |
|-----|---------|-------------|
| `Base_Damage` | `0.5` | Flat bonus added to the rank multiplier |
| `Rank_Damage_Multiplier` | `1.0` | Additional damage per rank |

---

### Cripple

**Ranks:** 4

Cripple is a passive sub-skill that gives a chance to inflict Slowness on a target whenever you land a mace hit. The activation chance is multiplied by your attack strength (charge level). Cripple will not activate if the target already has Slowness applied.

The Slowness level and duration differ for players versus mobs:

| Target | Slowness level | Duration |
|--------|---------------|---------|
| Players | Slowness II   | 1 s (20 ticks) |
| Mobs    | Slowness III  | 1.5 s (30 ticks) |

| Rank | Unlock level | Activation chance |
|------|-------------|-------------------|
| 1    | 50          | 10 %              |
| 2    | 200         | 15 %              |
| 3    | 400         | 20 %              |
| 4    | 800         | 33 %              |

**Config key** (`advanced.yml` under `Skills.Maces.Cripple`):

| Key | Default |
|-----|---------|
| `Chance_To_Apply_On_Hit.Rank_1` | `10` |
| `Chance_To_Apply_On_Hit.Rank_2` | `15` |
| `Chance_To_Apply_On_Hit.Rank_3` | `20` |
| `Chance_To_Apply_On_Hit.Rank_4` | `33` |

---

### Maces Limit Break

**Ranks:** 10

Maces Limit Break is a passive sub-skill that adds bonus damage against players in PvP. The bonus equals the player's current rank and is reduced by the quality of the defender's armour:

| Defender armour quality | Damage modifier |
|------------------------|----------------|
| 0 - 4 (e.g. leather) | x0.25 |
| 5 - 8 (e.g. iron) | x0.50 |
| 9 - 12 (e.g. chainmail) | x0.75 |
| > 12 (e.g. diamond/netherite) | x1.00 |

By default, Limit Break only applies in PvP. PvE can be enabled via `Skills.General.LimitBreak.AllowPVE: true` in `advanced.yml` (default: `false`). Against mobs, no armour-quality reduction is applied -- the full x1.00 modifier always applies.

| Rank | Unlock level |
|------|-------------|
| 1    | 100         |
| 2    | 200         |
| 3    | 300         |
| 4    | 400         |
| 5    | 500         |
| 6    | 600         |
| 7    | 700         |
| 8    | 800         |
| 9    | 900         |
| 10   | 1000        |

See the [Limit Break](/skills/limit-break) page for details on armour quality scores by material.

---

## Commands

| Command | Description |
|---------|-------------|
| `/maces` | Display your Maces skill stats and sub-skill information. |
| `/mctop maces` | View the Maces leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Limit Break](/skills/limit-break): armor-scaling bonus damage shared by every combat skill
- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
