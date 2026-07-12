---
title: World Blacklist
description: Information about the world blacklist feature for mcMMO
published: true
date: 2026-07-12T00:00:00.000Z
tags: blacklist, config
editor: markdown
dateCreated: 2022-07-17T22:33:56.252Z
---

# World Blacklist

The World Blacklist feature allows server administrators to disable mcMMO entirely in specific worlds. When a world is blacklisted, players in that world will not gain XP, skills will not function, and abilities will be unavailable.

## Configuration

The world blacklist is a plain-text file, `world_blacklist.txt`, in the mcMMO plugin folder. It is created automatically if it does not already exist. List one world name per line for each world you want to disable mcMMO in.

> Changes to `world_blacklist.txt` require a server restart to take effect.
{.is-warning}

## WorldGuard Integration

If you have WorldGuard installed, mcMMO also supports per-region control via WorldGuard flags. This gives you finer control than the world blacklist, you can disable mcMMO in specific regions rather than entire worlds.

See the [WorldGuard Integration](/plugin-integration/worldguard) page for the full list of supported flags and usage instructions.
