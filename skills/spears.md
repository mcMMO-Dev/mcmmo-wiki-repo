---
title: Spears
description: "Information about the Spears skill."
published: true
date: 2024-11-24T01:59:07.533Z
tags: spears, skills
editor: markdown
dateCreated: 2024-11-24T01:59:07.533Z
---

# Spears

The Spears skill governs combat with spears. XP is earned by striking mobs or players with a spear. Levelling Spears unlocks passive damage bonuses, a speed-on-hit effect, and a PvP damage multiplier.

## XP Gain

XP is granted each time a spear strike lands on a mob or player. The amount is determined by the target's entity type, following the same combat XP table used by other weapon skills.

## Sub-Skills

### Spear Mastery

**Ranks:** 8

Spear Mastery is a passive sub-skill that adds a flat damage bonus to every spear hit. The bonus increases by 0.4 HP per rank.

| Rank | Unlock level | Bonus damage (HP) |
|------|-------------|-------------------|
| 1    | 5           | 0.4               |
| 2    | 15          | 0.8               |
| 3    | 30          | 1.2               |
| 4    | 45          | 1.6               |
| 5    | 60          | 2.0               |
| 6    | 75          | 2.4               |
| 7    | 90          | 2.8               |
| 8    | 100         | 3.2               |

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
| 2    | 10          | 10 %              | 4 s     |
| 3    | 15          | 15 %              | 6 s     |
| 4    | 20          | 20 %              | 8 s     |
| 5    | 25          | 25 %              | 10 s    |
| 6    | 40          | 30 %              | 12 s    |
| 7    | 50          | 35 %              | 14 s    |
| 8    | 60          | 40 %              | 16 s    |
| 9    | 80          | 45 %              | 18 s    |
| 10   | 95          | 50 %              | 20 s    |

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
| 1    | 10          |
| 2    | 20          |
| 3    | 30          |
| 4    | 40          |
| 5    | 50          |
| 6    | 60          |
| 7    | 70          |
| 8    | 80          |
| 9    | 90          |
| 10   | 100         |

---

## Commands

| Command | Description |
|---------|-------------|
| `/spears` | Display your Spears skill stats and sub-skill information. |
| `/mctop spears` | View the Spears leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |
