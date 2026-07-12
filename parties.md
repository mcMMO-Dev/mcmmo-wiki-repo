---
title: Parties
description: "Information about the mcMMO party system."
published: true
date: 2026-07-12T00:00:00.000Z
tags: parties, party, mcmmo
editor: markdown
dateCreated: 2025-01-01T00:00:00.000Z
---

# Parties

mcMMO parties are player-formed groups that grow stronger as their members earn experience. Once a party levels up, members unlock additional features such as party chat, teleport, alliances, and shared XP or item drops. Parties are tracked entirely by mcMMO and are independent of other party plugins.

## At a glance

| | |
|---|---|
| **Created with** | `/party create <name>` |
| **Levels up by** | every party member's individual XP gain |
| **Default level cap** | 10 |
| **Default maximum size** | unlimited |
| **Default friendly fire** | off (PvP between party members disabled) |
| **Default share range** | 75 blocks |

## Joining and managing a party

The full party command set lives under `/party <subcommand>`. The most common subcommands:

| Command | Description |
|---------|-------------|
| `/party create <name>` | Create a new party. |
| `/party create <name> <password>` | Create a password-locked party. |
| `/party join <player>` | Request to join the party of `<player>`. |
| `/party accept` | Accept an outstanding invite. |
| `/party quit` | Leave your current party. |
| `/party invite <player>` | Invite another player to your party. |
| `/party kick <player>` | (Leader) remove a member from the party. |
| `/party owner <player>` | (Leader) transfer ownership to another member. |
| `/party rename <name>` | (Leader) rename the party. |
| `/party lock` / `unlock` | (Leader) toggle whether new players can join without an invite. |
| `/party password <password>` | (Leader) set or change the join password. |
| `/party disband` | (Leader) disband the party. |
| `/party teleport <player>` | Teleport to a member (requires Teleport feature unlocked). |
| `/party chat` | Toggle party chat mode. |
| `/party itemshare <type>` | Configure item sharing (NONE / EQUAL / RANDOM, by category). |
| `/party xpshare <mode>` | Configure XP sharing (NONE or EQUAL). |
| `/party alliance <party>` | Form / accept an alliance with another party. |
| `/party ?` | Show the full subcommand list. |

> Use `/party info` (or just `/party`) to view your current party, members, level, and which features are unlocked.
{.is-info}

## Party levelling

A party gains XP every time one of its members earns individual mcMMO XP. The party XP curve uses the regular skill XP formula multiplied by `(online member count + Xp_Curve_Modifier)`, so a larger party levels its party slightly faster -- but each individual contributes the same amount.

Reaching certain party levels unlocks new features:

| Party level | Feature unlocked | Config key (`config.yml` → `Party.Leveling`) |
|------------:|------------------|----------------------------------------------|
| 1 | Party Chat (`/p`, `/party chat`) | `Chat_UnlockLevel` (default `1`) |
| 2 | Party Teleport (`/party teleport`) | `Teleport_UnlockLevel` (default `2`) |
| 5 | Alliances (`/party alliance`) | `Alliance_UnlockLevel` (default `5`) |
| 8 | Item Share | `ItemShare_UnlockLevel` (default `8`) |
| 10 | XP Share | `XpShare_UnlockLevel` (default `10`) |

The level cap defaults to `10` (`Party.Leveling.Level_Cap`) and can be raised to extend levelling beyond the final feature unlock if you want a long-term progression goal.

## Sharing

### XP Share

When XP Share is unlocked and set to `EQUAL`, any mcMMO XP a party member earns is split equally between all eligible party members within range. A share bonus is then applied to the total so that sharing offsets some of the efficiency loss of splitting. The bonus multiplier is `ExpShare_bonus_base` plus `ExpShare_bonus_increase` for each sharing member, up to a maximum of `ExpShare_bonus_cap`.

| Config key (`config.yml` → `Party.Sharing`) | Default | Description |
|---------------------------------------------|---------|-------------|
| `ExpShare_bonus_base` | `1.1` | Base multiplier applied to shared XP |
| `ExpShare_bonus_increase` | `1.05` | Added to the multiplier for each sharing member |
| `ExpShare_bonus_cap` | `1.5` | Maximum total share multiplier |
| `Range` | `75.0` | Maximum block distance between members for sharing to trigger |

> A member must be within `Range` blocks of the earning member to receive a share. Members outside the range get nothing for that XP gain.
{.is-info}

### Item Share

Item Share routes drops from mob kills and (optionally) from gathering skills into the shared pool. It can be configured per category (loot, mining, herbalism, woodcutting, misc) and per mode (`NONE`, `EQUAL`, `RANDOM`). Use `/party itemshare` to set each category at runtime.

`EQUAL` awards each item in the stack through a fairness-weighted lottery that favours members who have received less, so drops even out across the party over time. `RANDOM` picks a random recipient independently for each item in the stack.

## Party features in detail

| Feature | What it does |
|---------|--------------|
| **Chat** | A separate chat channel visible only to party members. Toggled by `/party chat` or sent ad-hoc with `/p <message>`. |
| **Teleport** | `/party teleport <player>` warps you to a named party member after a short cast and cooldown. Subject to the per-player cooldown configured in `config.yml`. |
| **Alliance** | Two parties may ally. Allied party members do not damage each other (when friendly-fire is off). |
| **Item Share** | Mob-drop and gathering-drop items are distributed to in-range party members according to the configured per-category mode. |
| **XP Share** | mcMMO skill XP is split between all in-range party members, with the small share bonus described above. |

## Server administrator settings

The main party-system toggles live under `Party:` in `config.yml`:

| Config key | Default | Description |
|------------|---------|-------------|
| `Party.FriendlyFire` | `false` | If `true`, party members can damage each other. |
| `Party.MaxSize` | `-1` | Maximum members per party (`-1` = unlimited). |
| `Party.AutoKick_Interval` | `12` | Hours between automatic inactive-member kicks (`0` = at server start only, `-1` = disabled). |
| `Party.Old_Party_Member_Cutoff` | `7` | Days of inactivity before a member is auto-kicked. |
| `Party.Leveling.Level_Cap` | `10` | Maximum party level (also controls when XP share unlocks). |
| `Party.Leveling.Xp_Curve_Modifier` | `3` | Added to the member count when computing the party-level XP requirement. |
| `Party.Leveling.Near_Members_Needed` | `false` | If `true`, the earning member must have at least one party member nearby to grant party XP. |
| `Party.Leveling.Inform_All_Party_Members_On_LevelUp` | `false` | Send party-level-up notifications to every member instead of only the earner. |
| `Party.Enabled` *(in `party.yml`)* | `true` | Master switch for the entire party system. Set to `false` to disable parties on the server. |

## Permissions

The `mcmmo.commands.party` permission node tree covers every party subcommand. Some highlights:

| Permission | Grants |
|------------|--------|
| `mcmmo.commands.party` | Use the `/party` command at all. |
| `mcmmo.commands.party.chat` | Toggle / use party chat. |
| `mcmmo.commands.party.teleport` | Use `/party teleport`. |
| `mcmmo.commands.party.alliance` | Use `/party alliance`. |
| `mcmmo.commands.party.itemshare` | Use `/party itemshare`. |
| `mcmmo.commands.party.xpshare` | Use `/party xpshare`. |

See [Permissions](/permissions) for the complete list.

## See Also

- [Commands](/Commands): full command reference, including `/party` subcommands
- [Permissions](/permissions)
- [Configuration](/config)
