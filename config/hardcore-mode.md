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

Hardcore Mode is configured in `config.yml` under the hardcore section. You can:

- Enable or disable hardcore mode globally
- Set the percentage of levels or XP lost on death
- Configure which skills are affected

> Changes to `config.yml` require a server restart to take effect.
{.is-warning}

## How It Works

When a player dies with Hardcore Mode enabled:

- A percentage of their skill levels or XP is removed across applicable skills
- The exact amount lost depends on the configured percentage in `config.yml`
- This applies to deaths from any cause (mobs, players, environment)

## Vampirism Interaction

Hardcore Mode can interact with the [Vampirism](/config/vampirism) setting. When both are enabled, skill levels or XP lost by the dying player may be transferred to their killer (if killed by another player).
