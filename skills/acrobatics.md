---
title: Acrobatics
description: "Information about the Acrobatics skill."
published: true
date: 2026-07-12T00:00:00.000Z
tags: skills, acrobatics
editor: markdown
dateCreated: 2022-07-16T20:35:16.605Z
---

# Acrobatics

The Acrobatics skill rewards graceful movement. It grants a chance to negate fall damage (Roll / Graceful Roll) and a chance to halve incoming attack damage (Dodge).

> Unlike most mcMMO skills, Acrobatics gains XP through two separate paths: fall damage awards XP directly (no sub-skill needs to proc), but Roll XP and Dodge XP are only awarded when those sub-skills successfully activate.
{.is-info}

## At a glance

| | |
|---|---|
| **Category** | Passive / defensive |
| **Primary tool** | None (triggered by movement / damage) |
| **Super ability** | None |
| **Parent skill(s)** | None |
| **Child skill(s)** | None |

> **Compared to vanilla:** Feather Falling reduces fall damage by a fixed percentage. Acrobatics' Roll and Graceful Roll instead have a *chance* to fully cancel the fall damage, scaling with skill level. Both can stack, Feather Falling reduces the incoming damage before mcMMO checks for a roll.
{.is-info}

## XP Gain

| Source | XP formula |
|--------|-----------|
| Taking fall damage (no roll) | `600 × damage taken (HP)` |
| Successful Roll or Graceful Roll | `600 × damage that would have been taken (HP)` |
| Successful Dodge | `800 × damage dodged (HP)` |

> mcMMO multiplies fall XP by `FeatherFall_Multiplier` (default 2.0) when you wear boots enchanted with Feather Falling, at any level. The multiplier applies to the damage actually taken, and Feather Falling also lowers that damage, so the two effects offset each other. At Feather Falling IV the offset is nearly complete and XP at most fall heights stays close to the no-enchant value; lower enchantment levels reduce damage less, so they land between roughly equal and nearly double XP. A true doubling only happens on falls large enough that the reduced damage still reaches the 20 HP clamp.
{.is-info}

### XP from Falls

Fall and Roll XP are calculated from the damage taken, capped at 20 HP. A fall that would deal 20 or more HP of damage therefore awards the same XP; only Dodge XP is uncapped.

The table below shows approximate XP earned per fall at various fall heights, without armor enchantments:

| Blocks fallen | Damage (HP) | XP |
|--------------|------------|-----|
| 4 | 1 | 600 |
| 8 | 5 | 3000 |
| 12 | 9 | 5400 |
| 16 | 13 | 7800 |
| 24 | 21 (capped at 20) | 12000 |

> Values assume no armor damage reduction, no potions, and no armor enchantments. Actual XP scales with actual damage taken.
{.is-warning}

### Anti-Exploit

The following protections prevent AFK acrobatics farming (configurable in `experience.yml`):

- Holding an Ender Pearl in either hand, or being inside a vehicle, suppresses fall XP.
- Landing repeatedly on the same spot triggers a diminishing-returns lockout.
- After any successful Roll, a 3-second cooldown applies before another Roll grants XP. Additional falls before the cooldown expires extend it by 10 seconds, plus 1 extra second per subsequent fall.

```yml
ExploitFix:
    Acrobatics: true
```

Setting `ExploitFix.Acrobatics` to `false` disables all of the above protections. Players can then repeatedly trigger fall damage and Roll from the same location indefinitely, accumulating XP without engaging in normal gameplay. This is intended for servers that deliberately allow accelerated levelling or do not mind AFK farming.

Dodge XP has its own protection: a single mob grants Dodge XP for up to **6 dodges** and recovers after **60 seconds** without being dodged, so a trapped mob cannot be used as an endless XP source.

```yml
ExploitFix:
    AcrobaticsDodgeXpFarming: true
```

Setting `ExploitFix.AcrobaticsDodgeXpFarming` to `false` disables the Dodge XP limit.

## Sub-Skills

### Roll

**Ranks:** 0 (always available, no unlock level)

Roll gives a chance to negate fall damage when landing. A normal Roll negates up to **7 HP** of fall damage; a **Graceful Roll** (activated by sneaking while falling) doubles the protection cap to **14 HP** and also doubles the proc chance.

The proc chance scales linearly, reaching **100%** at level 1000.

| Level | Roll chance | Graceful Roll chance | Max damage negated (Roll) | Max damage negated (Graceful Roll) |
|-------|------------|---------------------|--------------------------|-----------------------------------|
| 250 | 25% | 50% | 7 HP | 14 HP |
| 500 | 50% | 100% | 7 HP | 14 HP |
| 750 | 75% | 100% | 7 HP | 14 HP |
| 1000 | 100% | 100% | 7 HP | 14 HP |

**Config keys** (`advanced.yml` under `Skills.Acrobatics.Roll` / `GracefulRoll`):

| Key | Default | Description |
|-----|---------|-------------|
| `Roll.ChanceMax` | `100.0` | Maximum Roll proc chance (%) at MaxBonusLevel |
| `Roll.MaxBonusLevel.RetroMode` | `1000` | Skill level at which max Roll chance is reached |
| `Roll.DamageThreshold` | `7.0` | Maximum HP of fall damage negated by a normal Roll |
| `GracefulRoll.DamageThreshold` | `14.0` | Maximum HP of fall damage negated by a Graceful Roll |

---

### Dodge

**Ranks:** 1, Unlocks at level 1

Dodge gives a chance to halve incoming damage from attacks and other harmful sources. The proc chance scales linearly from 0% at level 0 to **20%** at level 1000.

Dodge will **not** proc if the halved damage would still be lethal (the check uses the reduced value). After a player respawns, there is a short cooldown before Dodge can award XP again.

By default, Dodge **does** apply to lightning strikes. To stop Dodge from reducing lightning damage, set `Prevent_Dodge_Lightning` to `true` in `config.yml` (it ships as `false`):

```yml
Skills:
    Acrobatics:
        Prevent_Dodge_Lightning: true
```

**Config keys** (`advanced.yml` under `Skills.Acrobatics.Dodge`):

| Key | Default | Description |
|-----|---------|-------------|
| `ChanceMax` | `20.0` | Maximum Dodge proc chance (%) at MaxBonusLevel |
| `MaxBonusLevel.RetroMode` | `1000` | Skill level at which max chance is reached |
| `DamageModifier` | `2.0` | Divisor applied to incoming damage on proc (50% reduction) |

---

## Commands

| Command | Description |
|---------|-------------|
| `/acrobatics` | Display your Acrobatics skill stats and sub-skill information. |
| `/mctop acrobatics` | View the Acrobatics leaderboard. |
| `/mcrank` | Show your rank on every skill leaderboard. |

## See Also

- [Skill summary](/skills)
- [Commands](/Commands)
- [Permissions](/permissions)
- [Configuration](/config)
