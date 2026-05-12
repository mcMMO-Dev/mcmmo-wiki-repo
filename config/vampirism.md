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

Vampirism is configured in `config.yml` under the vampirism section. You can:

- Enable or disable vampirism globally
- Set the percentage of levels or XP transferred on a PvP kill
- Configure which skills are affected

> Changes to `config.yml` require a server restart to take effect.
{.is-warning}

## How It Works

When a player is killed by another player with Vampirism enabled:

- A percentage of the victim's skill levels or XP is removed
- That amount is transferred to the attacker
- This only applies to player-vs-player kills, not mob kills

## Hardcore Mode Interaction

Vampirism and [Hardcore Mode](/config/hardcore-mode) are independent — each can be enabled without the other. When both are enabled, a killed player suffers both penalties separately: the killer first steals a portion of the victim's levels via Vampirism, and then the victim loses an additional portion of their levels as the Hardcore death penalty.
