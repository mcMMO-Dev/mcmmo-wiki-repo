---
title: World Blacklist
description: Information about the world blacklist feature for mcMMO
published: true
date: 2024-11-24T01:59:07.533Z
tags: blacklist, config
editor: markdown
dateCreated: 2022-07-17T22:33:56.252Z
---

# World Blacklist

The World Blacklist feature allows server administrators to disable mcMMO entirely in specific worlds. When a world is blacklisted, players in that world will not gain XP, skills will not function, and abilities will be unavailable.

## Configuration

The world blacklist is configured in `config.yml`. Add the names of worlds you want to disable mcMMO in to the blacklist section.

> Changes to `config.yml` require a server restart to take effect.
{.is-warning}

## WorldGuard Integration

If you have WorldGuard installed, mcMMO also supports per-region control via WorldGuard flags. This gives you finer control than the world blacklist, you can disable mcMMO in specific regions rather than entire worlds.

See the [WorldGuard Integration](/plugin-integration/worldguard) page for the full list of supported flags and usage instructions.
