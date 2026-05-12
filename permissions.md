---
title: Permissions
description: mcMMO permissions info
published: true
date: 2024-11-24T01:48:31.847Z
tags: config, perks, permissions
editor: markdown
dateCreated: 2022-07-17T22:30:51.370Z
---

# Permissions

mcMMO permission nodes are set to sensible default values out of the box. Every player automatically receives `mcmmo.defaults`, which grants access to all standard mcMMO features. Server operators automatically receive `mcmmo.defaultsop`, which adds admin-level commands. You only need to configure permissions manually if your permission plugin denies all nodes by default.

The authoritative source for all permissions is [plugin.yml](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/plugin.yml) in the mcMMO source.

## Default Permission Groups

| Permission | Default | Description |
|------------|---------|-------------|
| `mcmmo.defaults` | All players | Grants standard player access: party chat, all skills, level-up broadcasts, MOTD, and default commands. |
| `mcmmo.defaultsop` | Operators | Grants admin chat, admin commands, all items, and all tools on top of defaults. |
| `mcmmo.all` | None | Grants everything: admin, bypass, all commands, defaults, defaultsop, all party perks, all perks. Equivalent to `mcmmo.*`. |

## Key Permission Nodes

### Player Permissions (included in `mcmmo.defaults`)
- `mcmmo.skills.all` — Access to all mcMMO skills
- `mcmmo.chat.partychat` — Use party chat
- `mcmmo.chat.colors` — See mcMMO chat colors
- `mcmmo.broadcast.levelup` — Receive level-up broadcast messages
- `mcmmo.motd` — See the mcMMO MOTD
- `mcmmo.commands.defaults` — Access to standard player commands

### Operator Permissions (included in `mcmmo.defaultsop`)
- `mcmmo.chat.adminchat` — Use admin chat
- `mcmmo.commands.defaultsop` — Access to operator-level commands
- `mcmmo.item.all` — Access to all mcMMO items
- `mcmmo.tools.all` — Access to all mcMMO tools

### Admin Permissions (included in `mcmmo.all`)
- `mcmmo.admin` — Full admin access
- `mcmmo.bypass.all` — Bypass all mcMMO restrictions

## Ability Permissions

Individual abilities can be granted or denied using the pattern:

```
mcmmo.ability.<skill>.<ability>
```

For example:
- `mcmmo.ability.swords.serrated_strikes`
- `mcmmo.ability.mining.super_breaker`
- `mcmmo.ability.axes.skull_splitter`

## Command Permissions

Individual commands follow the pattern:

```
mcmmo.commands.<command>
```

For example:
- `mcmmo.commands.mctop`
- `mcmmo.commands.mmoedit`
- `mcmmo.commands.mcremove`

## Perk Permissions

Perk permissions grant players special bonuses so long as the permission node is active. They follow the pattern:

```
mcmmo.perks.<perk>
```

Use `mcmmo.perks.*` to grant all perks. Perks can include things like double XP rates or reduced cooldowns, configurable in `advanced.yml`.

## Limit Break Permissions

Each combat skill's Limit Break ability can be individually controlled:

```
mcmmo.ability.<skill>.limit_break
```

For example:
- `mcmmo.ability.swords.swords_limit_break`
- `mcmmo.ability.axes.axes_limit_break`
- `mcmmo.ability.archery.archery_limit_break`
