---
title: Acrobatics
description: "Information about the Acrobatics skill."
published: true
date: 2026-07-11T00:00:00.000Z
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
| Taking fall damage (no roll) | `120 × damage taken (HP)` |
| Successful Roll or Graceful Roll | `80 × damage that would have been taken (HP)` |
| Successful Dodge | `120 × damage dodged (HP)` |

> The Feather Falling enchantment doubles Acrobatics XP earned from falls regardless of enchantment level, but it also reduces base fall damage, so both effects combine.
{.is-info}

### XP from Falls

The table below shows approximate XP earned per fall at various fall heights, with and without Feather Falling IV:

| Blocks fallen | Damage (HP) | XP (no FF) | XP (Feather Falling IV) |
|--------------|------------|-----------|------------------------|
| 4 | 2 | 240 | 480 |
| 8 | 10 | 1200 | 2400 |
| 12 | 18 | 2160 | 4320 |
| 16 | 26 | 3120 | 6240 |
| 24 | 42 | 5040 | 10080 |

> Values assume no armor damage reduction, no potions, and no enchantments other than Feather Falling where noted. Actual XP scales with actual damage taken.
{.is-warning}

### Anti-Exploit

The following protections prevent AFK acrobatics farming (configurable in `experience.yml`):

- A player holding an Ender Pearl while inside a vehicle does not gain XP from falling.
- Teleporting starts a 5-second cooldown during which fall XP is suppressed.
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

The proc chance scales linearly: 1% per level, reaching **100%** at level 1000.

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

By default, Dodge does not apply to lightning strikes. This can be changed in `config.yml`:

```yml
Skills:
    Acrobatics:
        Prevent_Dodge_Lightning: false
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
