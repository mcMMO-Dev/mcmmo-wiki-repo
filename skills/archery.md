---
title: Archery
description: "Information about the Archery skill."
published: true
date: 2024-11-24T01:44:06.678Z
tags: archery, skills
editor: markdown
dateCreated: 2022-07-16T22:04:13.180Z
---

# Archery

The Archery skill enhances combat with bows. Levelling Archery boosts arrow damage (Skill Shot), gives a chance to disorient enemy players with Nausea (Daze), and lets you recover arrows from slain mobs (Arrow Retrieval). Against particularly tough opponents, Archery Limit Break adds bonus damage on top.

## At a glance

| | |
|---|---|
| **Category** | Combat (ranged) |
| **Primary tool** | Bow |
| **Super ability** | Explosive Shot |
| **Parent skill(s)** | None |
| **Child skill(s)** | None |

## XP Gain

XP is earned each time an arrow deals damage to a mob or player. The XP awarded is multiplied by two factors:

- **Bow draw force:** arrows shot at full draw give maximum XP. The multiplier is `min(bowForce × 2.0, 1.0)`, so you only need to draw the bow halfway (force ≥ 0.5) to earn full XP.
- **Distance:** targets hit from farther away grant more XP. The multiplier is `1 + min(distance, 50) × 0.025`, capping at **2.25×** at 50 or more blocks.

Both multipliers are applied together: `totalXP = baseXP × forceMultiplier × distanceMultiplier`.

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

### Skill Shot

**Ranks:** 20, Unlocks at level 1

Skill Shot passively increases the damage dealt by every arrow. The bonus is a percentage of the arrow's base damage and scales with rank; higher ranks are unlocked as you level up.

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

The total damage is capped at `baseDamage + MaxDamage` regardless of rank, preventing extreme values from causing one-shot kills.

**Config keys** (`advanced.yml` under `Skills.Archery.SkillShot`):

| Key | Default | Description |
|-----|---------|-------------|
| `RankDamageMultiplier` | `10.0` | Percentage bonus per rank |
| `MaxDamage` | `9.0` | Maximum bonus HP that can be added to any arrow |

---

### Daze

**Ranks:** 0 (passive, no rank unlock), Active from level 1

Daze is a passive chance proc that triggers when an arrow hits a **player**. It has no effect on mobs. When Daze triggers:

- The target's view direction is forcibly rotated to a random pitch.
- The target receives **Nausea** for 10 seconds (200 ticks).
- An additional **4 HP (2 hearts)** of bonus damage is dealt.

The proc chance scales linearly from 0% at level 0 to **50%** at level 1000 and beyond.

**Config keys** (`advanced.yml` under `Skills.Archery.Daze`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `50.0` | Maximum proc chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which maximum chance is reached |
| `BonusDamage` | `4.0` | Bonus HP dealt when Daze triggers |

> Daze only affects players. It has no effect on mobs.
{.is-warning}

---

### Arrow Retrieval

**Ranks:** 1, Unlocks at level 1

Arrow Retrieval gives a passive chance to recover arrows from mobs you kill with a bow. When it procs, the arrows that hit the mob are dropped at the mob's death location. Arrows shot with the **Infinity** enchantment cannot be retrieved.

The retrieval chance scales linearly from 0% at level 0 to **100%** at level 1000.

**Config keys** (`advanced.yml` under `Skills.Archery.ArrowRetrieval`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `100.0` | Maximum retrieval chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which maximum chance is reached |

---

### Archery Limit Break

**Ranks:** 10

Archery Limit Break is a passive sub-skill that adds bonus damage to arrow hits against players who have high armour values. The bonus scales with rank and is modified by the quality of the defender's armour. By default it only applies in PvP; enabling `Skills.General.LimitBreak.AllowPVE` in `advanced.yml` also activates it against mobs.

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
| `/archery` | Display your Archery skill stats and sub-skill information. |
| `/mctop archery` | View the Archery leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Limit Break](skills/limit-break.md): armor-scaling bonus damage shared by every combat skill
- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
