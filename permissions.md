---
title: Permissions
description: mcMMO permissions info
published: true
date: 2026-07-12T00:00:00.000Z
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
- `mcmmo.skills.all`, Access to all mcMMO skills
- `mcmmo.chat.partychat`, Use party chat
- `mcmmo.chat.colors`, See mcMMO chat colors
- `mcmmo.broadcast.levelup`, Receive level-up broadcast messages
- `mcmmo.motd`, See the mcMMO MOTD
- `mcmmo.commands.defaults`, Access to standard player commands

### Operator Permissions (included in `mcmmo.defaultsop`)
- `mcmmo.chat.adminchat`, Use admin chat
- `mcmmo.commands.defaultsop`, Access to operator-level commands
- `mcmmo.item.all`, Access to all mcMMO items
- `mcmmo.tools.all`, Access to all mcMMO tools

### Admin Permissions (included in `mcmmo.all`)
- `mcmmo.admin`, Full admin access
- `mcmmo.bypass.all`, Bypass all mcMMO restrictions

## Ability Permissions

Individual abilities can be granted or denied using the pattern:

```
mcmmo.ability.<skill>.<ability>
```

For example:
- `mcmmo.ability.swords.serratedstrikes`
- `mcmmo.ability.mining.superbreaker`
- `mcmmo.ability.axes.skullsplitter`

## Command Permissions

Individual commands follow the pattern:

```
mcmmo.commands.<command>
```

For example:
- `mcmmo.commands.mctop`
- `mcmmo.commands.mmoedit`
- `mcmmo.commands.mcremove`

Some nodes worth knowing about:
- `mcmmo.commands.xprate.show`, View the current XP rates with `/xprate` (granted by default)
- `mcmmo.commands.inspect.far`, Inspect far away players and offline players with `/inspect`

## Perk Permissions

Perk permissions grant players special bonuses so long as the permission node is active. They follow the pattern:

```
mcmmo.perks.<perk>
```

Use `mcmmo.perks.*` to grant all perks. Perks can include things like boosted XP rates or reduced ability cooldowns. Most perk strengths are fixed by which permission node a player holds.

The XP boost perks multiply a player's XP gains and come in several families. The percentage boosts are:

- `mcmmo.perks.xp.10percentboost.all`
- `mcmmo.perks.xp.25percentboost.all`
- `mcmmo.perks.xp.50percentboost.all`
- `mcmmo.perks.xp.150percentboost.all`

There are also flat-multiplier families, `mcmmo.perks.xp.double.all` (2x), `mcmmo.perks.xp.triple.all` (3x), and `mcmmo.perks.xp.quadruple.all` (4x), plus `mcmmo.perks.xp.customboost.all`, whose multiplier is set by `Experience_Formula.Custom_XP_Perk.Boost` in `experience.yml`.

Replace `.all` with a skill name to boost a single skill instead, e.g. `mcmmo.perks.xp.25percentboost.mining`.

## Limit Break Permissions

Each combat skill's Limit Break ability can be individually controlled. The node repeats the skill name with no separator:

```
mcmmo.ability.<skill>.<skill>limitbreak
```

For example:
- `mcmmo.ability.swords.swordslimitbreak`
- `mcmmo.ability.axes.axeslimitbreak`
- `mcmmo.ability.archery.archerylimitbreak`
- `mcmmo.ability.maces.maceslimitbreak`
- `mcmmo.ability.tridents.tridentslimitbreak`
