---
title: Crossbows
description: "Information about the Crossbows skill."
published: true
date: 2024-11-24T01:41:00.858Z
tags: crossbow, skills
editor: markdown
dateCreated: 2024-04-13T18:01:10.633Z
---

# Crossbows

> Crossbows is a newer skill that is still being expanded. Some features and balance may change in future releases. Join the [mcMMO Discord](https://discord.gg/mcmmo) for the latest news.
{.is-warning}

The Crossbows skill enhances combat with crossbows. Levelling Crossbows boosts bolt damage (Powered Shot), lets bolts ricochet off blocks (Trick Shot), and adds bonus damage against heavily armoured players (Crossbows Limit Break). XP is earned each time a crossbow bolt damages a mob or player.

## At a glance

| | |
|---|---|
| **Category** | Combat (ranged) |
| **Primary tool** | Crossbow |
| **Super ability** | None |
| **Parent skill(s)** | None |
| **Child skill(s)** | None |

## XP Gain

XP is earned each time a crossbow bolt deals damage to a mob or player. Like Archery, the XP is multiplied by a distance factor:

- **Distance:** targets hit from farther away grant more XP. The multiplier is `1 + min(distance, 50) × 0.025`, capping at **2.25×** at 50 or more blocks.

Unlike bows, crossbows do not have a draw-force multiplier (they are always fully loaded).

### XP Distance Multiplier Reference

| Distance to target (blocks) | XP multiplier |
|-----------------------------|--------------|
| 0 | 1.00× |
| 10 | 1.25× |
| 20 | 1.50× |
| 30 | 1.75× |
| 40 | 2.00× |
| 50+ | 2.25× (cap) |

## Sub-Skills

### Powered Shot

**Ranks:** 20, Unlocks at level 1

Powered Shot passively increases the damage dealt by every crossbow bolt. The bonus is a percentage of the bolt's base damage and scales with rank; higher ranks are unlocked as you level up.

| Rank | Unlock level | Damage bonus |
|------|-------------|--------------|
| 1 | 1 | +10% |
| 2 | 100 | +20% |
| 3 | 150 | +30% |
| 4 | 200 | +40% |
| 5 | 250 | +50% |
| 6 | 300 | +60% |
| 7 | 350 | +70% |
| 8 | 400 | +80% |
| 9 | 450 | +90% |
| 10 | 500 | +100% |
| 11 | 550 | +110% |
| 12 | 600 | +120% |
| 13 | 650 | +130% |
| 14 | 700 | +140% |
| 15 | 750 | +150% |
| 16 | 800 | +160% |
| 17 | 850 | +170% |
| 18 | 900 | +180% |
| 19 | 950 | +190% |
| 20 | 1000 | +200% |

**Formula:** `damage = min(baseDamage + bonusDamage, baseDamage + MaxDamage)`
where `bonusDamage = baseDamage × (rank × RankDamageMultiplier / 100)`.

Total damage is capped at `baseDamage + MaxDamage` regardless of rank.

**Config keys** (`advanced.yml` under `Skills.Crossbows.PoweredShot`):

| Key | Default | Description |
|-----|---------|-------------|
| `RankDamageMultiplier` | `10.0` | Percentage bonus per rank |
| `MaxDamage` | `9.0` | Maximum bonus HP that can be added to any bolt |

---

### Trick Shot

**Ranks:** 3, Unlocks at level 50

Trick Shot allows crossbow bolts to ricochet off solid blocks. When a bolt collides with a block surface, it spawns a new bolt with a reflected trajectory and continues toward whatever targets lie in the new direction. The maximum number of ricochets per original bolt equals the player's current Trick Shot rank.

| Rank | Unlock level | Max ricochets |
|------|-------------|--------------|
| 1 | 50 | 1 |
| 2 | 200 | 2 |
| 3 | 400 | 3 |

**Mechanics:**
- The reflected bolt inherits damage, critical status, pierce level, knockback, and potion effects from the original.
- Arrows shot with Infinity cannot be picked up after ricocheting.
- Very shallow-angle impacts (less than 45 degrees from the block normal) do not ricochet on the first bounce.
- Ricocheting bolts can deal damage and award XP normally.

---

### Crossbows Limit Break

**Ranks:** 10

Crossbows Limit Break is a passive sub-skill that adds bonus damage to crossbow hits against players who have high armour values. The bonus scales with rank and is modified by the quality of the defender's armour. By default it only applies in PvP; enabling `Skills.General.LimitBreak.AllowPVE` in `advanced.yml` also activates it against mobs.

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

The raw bonus equals the rank, then modified by the defender's armour quality score:

| Defender armour quality | Damage modifier |
|------------------------|----------------|
| 0 – 4 (e.g. leather) | ×0.25 |
| 5 – 8 (e.g. iron) | ×0.50 |
| 9 – 12 (e.g. chainmail) | ×0.75 |
| > 12 (e.g. diamond/netherite) | ×1.00 |

Against mobs (when PvE is enabled), the full ×1.00 modifier always applies. See the [Limit Break](/skills/limit-break) page for details on armour quality scores by material.

---

## Commands

| Command | Description |
|---------|-------------|
| `/crossbows` | Display your Crossbows skill stats and sub-skill information. |
| `/mctop crossbows` | View the Crossbows leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Limit Break](skills/limit-break.md): armor-scaling bonus damage shared by every combat skill
- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
