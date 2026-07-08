---
title: Tridents
description: "Information about the Tridents skill."
published: true
date: 2024-11-24T01:40:37.274Z
tags: skills, tridents
editor: markdown
dateCreated: 2024-04-13T18:14:01.830Z
---

# Tridents

> Tridents is a newer skill that is still being expanded. Some features and balance may change in future releases. Join the [mcMMO Discord](https://discord.gg/mcmmo) for the latest news.
{.is-warning}

The Tridents skill governs combat with tridents. XP is earned by striking mobs or players with a trident, both melee (close-range) and thrown (ranged) hits grant XP. Levelling Tridents unlocks passive damage bonuses that scale with your skill level.

## At a glance

| | |
|---|---|
| **Category** | Combat (melee + ranged) |
| **Primary tool** | Trident |
| **Super ability** | None |
| **Parent skill(s)** | None |
| **Child skill(s)** | None |

## XP Gain

XP is granted each time a trident strike lands on a mob or player. The amount is determined by the target's entity type, following the same combat XP table used by other weapon skills. Players can only grant XP if PvP XP is enabled in `experience.yml` (`PVP.Enabled: true`).

## Sub-Skills

### Impale

**Ranks:** 10

Impale is a passive sub-skill that adds a flat damage bonus to every trident hit.

- **Melee hits:** the bonus is multiplied by your attack strength (charge level), so a fully charged swing deals the full bonus while a quick-attack deals a fraction of it.
- **Thrown tridents:** the bonus is applied as a flat value with no attack-strength scaling.

**Damage bonus per rank:**

| Rank | Unlock level | Bonus damage (HP) |
|------|-------------|-------------------|
| 1    | 50          | 1.0               |
| 2    | 150         | 1.5               |
| 3    | 250         | 2.0               |
| 4    | 350         | 2.5               |
| 5    | 450         | 3.0               |
| 6    | 550         | 3.5               |
| 7    | 650         | 4.0               |
| 8    | 750         | 4.5               |
| 9    | 850         | 5.0               |
| 10   | 1000        | 5.5               |

**Formula:** `bonus = 1.0 + (rank − 1) × 0.5`

**Config keys** (`advanced.yml` under `Skills.Tridents.Impale`):

| Key | Default | Description |
|-----|---------|-------------|
| `Base_Damage` | `1.0` | Flat damage bonus at rank 1 |
| `Rank_Damage_Multiplier` | `0.5` | Additional damage added per rank beyond rank 1 |

---

### Tridents Limit Break

**Ranks:** 10

Tridents Limit Break is a passive sub-skill that adds bonus damage against targets wearing high-quality armor. The raw bonus equals the player's current rank. It is then modified by the target's total armor quality score. By default it only applies in PvP; enabling `Skills.General.LimitBreak.AllowPVE: true` in `advanced.yml` also activates it against mobs.

> Limit Break damage is also multiplied by your attack strength at the moment of the hit.
{.is-info}

| Rank | Unlock level | Raw bonus damage (HP) |
|------|-------------|----------------------|
| 1    | 100         | 1                    |
| 2    | 200         | 2                    |
| 3    | 300         | 3                    |
| 4    | 400         | 4                    |
| 5    | 500         | 5                    |
| 6    | 600         | 6                    |
| 7    | 700         | 7                    |
| 8    | 800         | 8                    |
| 9    | 900         | 9                    |
| 10   | 1000        | 10                   |

**Armor quality modifier:**

| Total armor quality score | Damage modifier |
|--------------------------|------------------|
| 0 – 4                    | ×0.25            |
| 5 – 8                    | ×0.50            |
| 9 – 12                   | ×0.75            |
| 13+                      | ×1.00            |

**Armor quality score per piece:**

| Armor material   | Score per piece |
|-----------------|------------------|
| Leather / Copper | 1               |
| Iron             | 2               |
| Gold / Chainmail | 3               |
| Diamond          | 6               |
| Netherite        | 12              |

See [Limit Break](/skills/limit-break) for full details on the damage formula and armor quality scoring.

---

## Commands

| Command | Description |
|---------|-------------|
| `/tridents` | Display your Tridents skill stats and sub-skill information. |
| `/mctop tridents` | View the Tridents leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Limit Break](/skills/limit-break): armor-scaling bonus damage shared by every combat skill
- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
