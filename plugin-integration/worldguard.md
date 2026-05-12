---
title: WorldGuard Integration
description: Information about mcMMO's WorldGuard flag support
published: true
date: 2026-05-11T00:00:00.000Z
tags: worldguard, plugin-integration, config
editor: markdown
dateCreated: 2026-05-11T00:00:00.000Z
---

# WorldGuard Integration

mcMMO supports [WorldGuard](https://enginehub.org/worldguard) for per-region control of mcMMO features. When WorldGuard is installed, mcMMO registers three custom `StateFlag` values that can be set on any WorldGuard region.

All three flags default to `allow`, meaning mcMMO behaves normally in regions where the flags are not explicitly set.

## Flags

| Flag | Default | Controls |
|------|---------|----------|
| `mcmmo` | allow | Skills, abilities, and XP gain. Disabling this flag suppresses all mcMMO functionality for players in the region. |
| `mcmmo-xp` | allow | XP gain only. Disabling this flag prevents players from earning mcMMO XP in the region while leaving skills and abilities functional. |
| `mcmmo-hardcore` | allow | Hardcore and Vampirism death penalties. Disabling this flag prevents hardcore stat loss and vampirism from triggering in the region. |

## Usage

Set flags on a region using the standard WorldGuard flag command:

```
/rg flag <region> mcmmo deny
/rg flag <region> mcmmo-xp deny
/rg flag <region> mcmmo-hardcore deny
```

Regions inherit the server-wide default (`allow`) when a flag is not explicitly set.

> WorldGuard flags provide finer-grained control than the [World Blacklist](/config/world-blacklist), which disables mcMMO for an entire world.
{.is-info}
