---
title: Hardcore Mode
description: Information about mcMMO's optional hardcore mode
published: true
date: 2024-11-24T01:59:07.533Z
tags: config, hardcore
editor: markdown
dateCreated: 2022-07-17T21:51:08.011Z
---

# Hardcore Mode

Hardcore Mode is an optional death penalty system in mcMMO. When enabled, players lose skill levels or XP when they die. This adds a risk-reward dynamic to gameplay, encouraging caution in dangerous situations.

## Configuration

Hardcore Mode is configured in `config.yml` under `Hardcore.Death_Stat_Loss`. There is no single global enable/disable switch — each skill is individually toggled. All skills are **disabled by default**, so Hardcore Mode has no effect until you explicitly enable at least one skill.

| Key | Default | Description |
|-----|---------|-------------|
| `Hardcore.Death_Stat_Loss.Penalty_Percentage` | `75.0` | Percentage of skill levels (above the threshold) removed on death. |
| `Hardcore.Death_Stat_Loss.Level_Threshold` | `0` | Levels at or below this value are protected — the penalty only applies to levels above the threshold. |
| `Hardcore.Death_Stat_Loss.Enabled.<SkillName>` | `false` | Enable the penalty for a specific skill, e.g. `Enabled.Mining: true`. |

> Changes to `config.yml` require a server restart to take effect.
{.is-warning}

## How It Works

When a player dies with Hardcore Mode enabled for at least one skill:

- For each enabled skill, a percentage of the player's levels **above** the threshold is removed.
- The formula is: `levelsLost = floor((skillLevel − levelThreshold) × penaltyPercentage / 100)`, with the fractional remainder converted to a proportional XP loss.
- This applies to deaths from any cause (mobs, players, environment).

## Vampirism Interaction

Hardcore Mode can interact with the [Vampirism](/config/vampirism) setting. When both are enabled, skill levels or XP lost by the dying player may be transferred to their killer (if killed by another player).
