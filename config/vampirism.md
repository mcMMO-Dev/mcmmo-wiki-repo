---
title: Vampirism
description: Information about mcMMO's optional vampirism setting
published: true
date: 2024-11-24T01:59:07.533Z
tags: config, vampirism, pvp
editor: markdown
dateCreated: 2022-07-17T21:52:03.092Z
---

# Vampirism

Vampirism is an optional PvP mechanic in mcMMO. When enabled, killing another player transfers some of their skill XP or levels to the attacker. This incentivizes PvP combat and creates a risk for players with high skill levels.

## Configuration

Vampirism is configured in `config.yml` under `Hardcore.Vampirism`. There is no single global enable/disable switch — each skill is individually toggled. All skills are **disabled by default**, so Vampirism has no effect until you explicitly enable at least one skill.

| Key | Default | Description |
|-----|---------|-------------|
| `Hardcore.Vampirism.Leech_Percentage` | `5.0` | Percentage of the victim's skill level stolen per PvP kill. |
| `Hardcore.Vampirism.Level_Threshold` | `0` | Victim must have more levels than this threshold in a skill before it can be stolen. |
| `Hardcore.Vampirism.Enabled.<SkillName>` | `false` | Enable vampirism for a specific skill, e.g. `Enabled.Swords: true`. |

> Changes to `config.yml` require a server restart to take effect.
{.is-warning}

## How It Works

When a player is killed by another player with Vampirism enabled for at least one skill:

- For each enabled skill, a percentage of the victim's total level is stolen and added directly to the killer's level.
- Vampirism only triggers on a skill if the victim's level is **at least half** the killer's level in that skill — low-level players cannot be farmed by high-level killers.
- The formula is: `levelsStolen = floor(victimSkillLevel × leechPercentage / 100)`, with the fractional remainder applied as XP.
- This only applies to player-vs-player kills, not mob kills.

## Hardcore Mode Interaction

Vampirism and [Hardcore Mode](/config/hardcore-mode) are independent, each can be enabled without the other. When both are enabled, a killed player suffers both penalties separately: the killer first steals a portion of the victim's levels via Vampirism, and then the victim loses an additional portion of their levels as the Hardcore death penalty.
