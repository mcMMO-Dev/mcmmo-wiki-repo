---
title: Spears
description: "Information about the Spears skill."
published: true
date: 2026-07-12T00:00:00.000Z
tags: spears, skills
editor: markdown
dateCreated: 2024-11-24T01:59:07.533Z
---

# Spears

The Spears skill governs combat with spears. XP is earned by striking mobs or players with a spear. Levelling Spears unlocks passive damage bonuses, a speed-on-hit effect, and a PvP damage multiplier.

## At a glance

| | |
|---|---|
| **Category** | Combat (melee) |
| **Primary tool** | Spear |
| **Super ability** | None |
| **Parent skill(s)** | None |
| **Child skill(s)** | None |

## XP Gain

XP is granted each time a spear strike lands on a mob or player. The amount is determined by the target's entity type, following the same combat XP table used by other weapon skills.

## Sub-Skills

### Spear Mastery

**Ranks:** 8

Spear Mastery is a passive sub-skill that adds bonus damage to every spear hit. The bonus increases by 0.4 HP per rank.

The bonus damage is multiplied by your attack strength (charge level), so fully charged hits deliver the full bonus shown below while quick-attacks deliver proportionally less.

| Rank | Unlock level | Bonus damage (HP) |
|------|-------------|-------------------|
| 1    | 50          | 0.4               |
| 2    | 150         | 0.8               |
| 3    | 300         | 1.2               |
| 4    | 450         | 1.6               |
| 5    | 600         | 2.0               |
| 6    | 750         | 2.4               |
| 7    | 900         | 2.8               |
| 8    | 1000        | 3.2               |

**Formula:** `bonus = rank × Rank_Damage_Multiplier`

**Config key** (`advanced.yml` under `Skills.Spears.SpearMastery`):

| Key | Default | Description |
|-----|---------|-------------|
| `Rank_Damage_Multiplier` | `0.4` | Damage added per rank |

---

### Momentum

**Ranks:** 10

Momentum is a passive sub-skill that gives a chance to gain **Speed III** when you land a spear hit. The activation chance and effect duration both scale with rank. Momentum will not activate if you already have a stronger or longer-lasting Speed effect.

The activation chance is multiplied by your attack strength (charge level), so fully charged hits roll the full chance while quick-attacks roll proportionally less.

| Rank | Unlock level | Activation chance | Duration |
|------|-------------|-------------------|---------|
| 1    | 1           | 5 %               | 2 s     |
| 2    | 100         | 10 %              | 4 s     |
| 3    | 150         | 15 %              | 6 s     |
| 4    | 200         | 20 %              | 8 s     |
| 5    | 250         | 25 %              | 10 s    |
| 6    | 400         | 30 %              | 12 s    |
| 7    | 500         | 35 %              | 14 s    |
| 8    | 600         | 40 %              | 16 s    |
| 9    | 800         | 45 %              | 18 s    |
| 10   | 950         | 50 %              | 20 s    |

**Config key** (`advanced.yml` under `Skills.Spears.Momentum`):

| Key | Default |
|-----|---------|
| `Chance_To_Apply_On_Hit.Rank_N` | 5 / 10 / 15 / 20 / 25 / 30 / 35 / 40 / 45 / 50 |

> Duration formula: `40 × rank` ticks. Speed III (amplifier 2) is always applied.
{.is-info}

---

### Spears Limit Break

**Ranks:** 10

Spears Limit Break is a passive sub-skill that adds bonus damage against players in PvP. The bonus equals the player's current rank and is reduced by the quality of the defender's armour:

| Defender armour quality | Damage multiplier |
|------------------------|-------------------|
| ≤ 4                    | 25 % (75 % nerf)  |
| 5 – 8                  | 50 %              |
| 9 – 12                 | 75 %              |
| > 12                   | 100 % (no nerf)   |

By default, Limit Break only applies in PvP. PvE can be enabled via `Skills.General.LimitBreak.AllowPVE: true` in `advanced.yml` (default: `false`). Against mobs, no armour-quality reduction is applied.

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

---

## Commands

| Command | Description |
|---------|-------------|
| `/spears` | Display your Spears skill stats and sub-skill information. |
| `/mctop spears` | View the Spears leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Limit Break](/skills/limit-break): armor-scaling bonus damage shared by every combat skill
- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
