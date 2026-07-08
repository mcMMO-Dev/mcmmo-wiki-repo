---
title: Unarmed
description: "Information about the Unarmed skill."
published: true
date: 2024-11-24T01:42:06.231Z
tags: skills, unarmed
editor: markdown
dateCreated: 2022-07-17T14:29:42.727Z
---

# Unarmed

The Unarmed skill enhances bare-handed combat. Levelling Unarmed unlocks passive damage bonuses (Steel Arm Style), a damage multiplier ability (Berserk), arrow deflection (Arrow Deflect), weapon disarming (Disarm), resistance to being disarmed (Iron Grip), passive block cracking (Block Cracker), and bonus damage against armored targets (Unarmed Limit Break).

## At a glance

| | |
|---|---|
| **Category** | Combat (melee) |
| **Primary tool** | Fists (empty hand) |
| **Super ability** | Berserk |
| **Parent skill(s)** | None |
| **Child skill(s)** | None |

## XP Gain

XP is earned based on the amount of damage dealt to mobs or players while fighting bare-handed (no weapon held). XP is proportional to damage dealt; heavier hits grant more XP.

## Sub-Skills

### Steel Arm Style

**Ranks:** 20

Steel Arm Style adds a flat HP bonus to every unarmed hit. It is always active once unlocked, there is no proc chance. The bonus scales with rank using the formula `0.5 + (rank / 2)`, with extra bonus added at ranks 18+ for a steeper curve.

| Rank | Unlock level | Bonus damage (HP) |
|------|-------------|-------------------|
| 1 | 1 | 1.0 |
| 2 | 100 | 1.5 |
| 3 | 150 | 2.0 |
| 4 | 200 | 2.5 |
| 5 | 250 | 3.0 |
| 6 | 300 | 3.5 |
| 7 | 350 | 4.0 |
| 8 | 400 | 4.5 |
| 9 | 450 | 5.0 |
| 10 | 500 | 5.5 |
| 11 | 550 | 6.0 |
| 12 | 600 | 6.5 |
| 13 | 650 | 7.0 |
| 14 | 700 | 7.5 |
| 15 | 750 | 8.0 |
| 16 | 800 | 8.5 |
| 17 | 850 | 9.0 |
| 18 | 900 | 10.5 |
| 19 | 950 | 12.0 |
| 20 | 1000 | 13.5 |

**Config keys** (`advanced.yml` under `Skills.Unarmed.SteelArmStyle`):

| Key | Default | Description |
|-----|---------|-------------|
| `Damage_Override` | `false` | When `true`, uses the per-rank `Override` values instead of the formula |
| `Override.Rank_N` | (see table) | Custom damage values per rank (only used when `Damage_Override: true`) |

---

### Berserk

**Ranks:** 1, Unlocks at level 50

Berserk is an active ability that must be armed by right-clicking while bare-handed and not looking at a block. When active, all unarmed hits deal **1.5× damage** multiplied by the current attack strength modifier.

Duration scales with your Unarmed level, starting at 3 seconds at level 50 and gaining 1 second every additional 50 levels, up to a default maximum of 1000 seconds.

| Unarmed Level | Duration |
|--------------:|---------:|
| 50            | 3s       |
| 100           | 4s       |
| 200           | 6s       |
| 500           | 12s      |
| 1000          | 22s      |
| 2000          | 42s      |

| Property | Key | Default | Description |
|----------|-----|---------|-------------|
| Unlock level | `skillranks.yml` → `Unarmed.Berserk.RetroMode.Rank_1` | `50` | Minimum skill level to unlock this ability |
| Cooldown | `config.yml` → `Abilities.Cooldowns.Berserk` | `240s` | Seconds before the ability can be activated again |
| Max duration | `config.yml` → `Abilities.Max_Seconds.Berserk` | `0` (no cap) | Per-ability duration ceiling in seconds. Only takes effect if lower than the global duration cap; 0 disables this cap entirely |
| Global duration cap | `advanced.yml` → `Skills.General.Ability.Length.RetroMode.CapLevel` | `1000s` | Maximum duration for all super abilities |

---

### Arrow Deflect

**Ranks:** 1, Unlocks at level 200

Arrow Deflect is a passive proc that triggers when a projectile (arrow, bolt, etc.) would hit you while bare-handed. On proc, the projectile is deflected and deals no damage. The proc chance scales linearly from 0% at level 0 to **50%** at level 1000.

**Config keys** (`advanced.yml` under `Skills.Unarmed.ArrowDeflect`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `50.0` | Maximum deflect chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which max chance is reached |

---

### Disarm

**Ranks:** 1, Unlocks at level 250

Disarm is a passive proc that triggers when you deal damage to another player bare-handed. On proc, the target''s held item is dropped at their location. If `AntiTheft` is enabled in `advanced.yml`, only the disarmed player can pick up their own item.

The proc chance scales linearly from 0% at level 0 to **33%** at level 1000. The chance is also multiplied by the attack strength modifier. Disarm can be prevented by the target''s Iron Grip proc.

**Config keys** (`advanced.yml` under `Skills.Unarmed.Disarm`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `33.0` | Maximum disarm chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which max chance is reached |
| `AntiTheft` | `false` | Restricts dropped item pickup to the disarmed player |

---

### Iron Grip

**Ranks:** 1, Unlocks at level 600

Iron Grip is a passive counter-proc that triggers when another player attempts to Disarm you. On proc, the Disarm is negated and both players are notified. The proc chance scales linearly from 0% at level 0 to **100%** at level 1000.

**Config keys** (`advanced.yml` under `Skills.Unarmed.IronGrip`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `100.0` | Maximum Iron Grip chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which max chance is reached |

---

### Block Cracker

**Ranks:** 0 (passive, no rank unlock required)

Block Cracker is a passive ability that automatically converts certain block types into their cracked variants when punched bare-handed. No proc chance is involved, the conversion happens every punch, provided the `Block_Cracker` permission is granted and the feature is enabled in `config.yml`.

Affected conversions:

| Input block | Output block |
|-------------|-------------|
| Stone Bricks | Cracked Stone Bricks |
| Infested Stone Bricks | Infested Cracked Stone Bricks |
| Deepslate Bricks | Cracked Deepslate Bricks |
| Deepslate Tiles | Cracked Deepslate Tiles |
| Polished Blackstone Bricks | Cracked Polished Blackstone Bricks |
| Nether Bricks | Cracked Nether Bricks |

---

### Unarmed Limit Break

**Ranks:** 10

Unarmed Limit Break is a passive sub-skill that adds bonus damage against targets wearing high-quality armor. The raw bonus equals the player's current rank. It is then modified by the target's total armor quality score. By default it only applies in PvP; enabling `Skills.General.LimitBreak.AllowPVE: true` in `advanced.yml` also activates it against mobs.

> Limit Break damage is also multiplied by your attack strength at the moment of the hit.
{.is-info}

| Rank | Unlock level | Raw bonus damage (HP) |
|------|-------------|----------------------|
| 1 | 100 | 1 |
| 2 | 200 | 2 |
| 3 | 300 | 3 |
| 4 | 400 | 4 |
| 5 | 500 | 5 |
| 6 | 600 | 6 |
| 7 | 700 | 7 |
| 8 | 800 | 8 |
| 9 | 900 | 9 |
| 10 | 1000 | 10 |

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
| `/unarmed` | Display your Unarmed skill stats and sub-skill information. |
| `/mctop unarmed` | View the Unarmed leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Limit Break](/skills/limit-break): armor-scaling bonus damage shared by every combat skill
- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
