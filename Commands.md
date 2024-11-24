---
title: Commands
description: mcMMO commands
published: true
date: 2024-11-24T02:50:12.570Z
tags: commands
editor: markdown
dateCreated: 2024-11-24T01:51:14.196Z
---

# mcMMO Commands

## Table of Contents

- [General Commands](#general-commands)
- [Skill Management](#skill-management)
- [Party Commands](#party-commands)
- [Chat Commands](#chat-commands)
- [Admin Commands](#admin-commands)
- [Miscellaneous Commands](#miscellaneous-commands)

---

## General Commands

These commands provide basic information and settings for mcMMO.

| Command      | Aliases   | Description                              | Permission               |
|--------------|-----------|------------------------------------------|--------------------------|
| `/mcmmo`     | None      | Shows a brief description of mcMMO.      | `mcmmo.commands.mcmmo`   |
| `/mmoinfo`   | `/mcinfo` | (WIP) Currently unfinished command to show detailed info for sub-skills.            | `mcmmo.commands.mmoinfo` |

---

## Skill Management

Manage and view your mcMMO skills, experience, and rankings.

| Command      | Aliases                        | Description                              | Permission                |
|--------------|--------------------------------|------------------------------------------|---------------------------|
| `/mctop`     | None                           | Shows mcMMO leaderboards.                | `mcmmo.commands.mctop`    |
| `/mcrank`    | None                           | Displays your mcMMO ranking.             | `mcmmo.commands.mcrank`   |
| `/mcstats`   | `/stats`                       | Shows your mcMMO stats and XP.           | `mcmmo.commands.mcstats`  |
| `/mmopower`  | `/mmopowerlevel`, `/powerlevel`| (WIP) Shows your powerlevel. | `mcmmo.commands.mmopower` |

### Skill Commands

View detailed information about specific skills:

| Command        | Aliases | Description                      | Permission                  |
|----------------|---------|----------------------------------|-----------------------------|
| `/excavation`  | None    | Detailed mcMMO Excavation skill info. | `mcmmo.commands.excavation` |
| `/herbalism`   | None    | Detailed mcMMO Herbalism skill info.  | `mcmmo.commands.herbalism`  |
| `/mining`      | None    | Detailed mcMMO Mining skill info.     | `mcmmo.commands.mining`     |
| `/woodcutting` | None    | Detailed mcMMO Woodcutting skill info.| `mcmmo.commands.woodcutting`|
| `/axes`        | None    | Detailed mcMMO Axes skill info.       | `mcmmo.commands.axes`       |
| `/archery`     | None    | Detailed mcMMO Archery skill info.    | `mcmmo.commands.archery`    |
| `/crossbows`   | None    | Detailed mcMMO Crossbows skill info.  | `mcmmo.commands.crossbows`  |
| `/swords`      | None    | Detailed mcMMO Swords skill info.     | `mcmmo.commands.swords`     |
| `/taming`      | None    | Detailed mcMMO Taming skill info.     | `mcmmo.commands.taming`     |
| `/tridents`    | None    | Detailed mcMMO Tridents skill info.   | `mcmmo.commands.tridents`   |
| `/unarmed`     | None    | Detailed mcMMO Unarmed skill info.    | `mcmmo.commands.unarmed`    |
| `/acrobatics`  | None    | Detailed mcMMO Acrobatics skill info. | `mcmmo.commands.acrobatics` |
| `/repair`      | None    | Detailed mcMMO Repair skill info.     | `mcmmo.commands.repair`     |
| `/fishing`     | None    | Detailed mcMMO Fishing skill info.    | `mcmmo.commands.fishing`    |
| `/smelting`    | None    | Detailed mcMMO Smelting skill info.   | `mcmmo.commands.smelting`   |
| `/alchemy`     | None    | Detailed mcMMO Alchemy skill info.    | `mcmmo.commands.alchemy`    |
| `/salvage`     | None    | Detailed mcMMO Salvage skill info.    | `mcmmo.commands.salvage`    |
| `/maces`       | None    | Detailed mcMMO Maces skill info.      | `mcmmo.commands.maces`      |

---

## Party Commands

Manage your party and interact with party members.

| Command    | Aliases          | Description                              | Permission                |
|------------|------------------|------------------------------------------|---------------------------|
| `/party`   | None             | Create or join a party.                  | `mcmmo.commands.party`    |
| `/ptp`     | None             | Teleport to a party member.              | `mcmmo.commands.ptp`      |
| `/partychat`| `/pc`, `/p`     | Toggle party chat or send party chat messages. | `mcmmo.chat.partychat` |

---

## Admin Chat Commands

Manage chat-related functionalities within mcMMO.

| Command        | Aliases     | Description                                         | Permission                  |
|----------------|-------------|-----------------------------------------------------|-----------------------------|
| `/adminchat`   | `/ac`, `/a` | Toggle Admin chat or send admin chat messages.      | `mcmmo.chat.adminchat`      |
| `/mcscoreboard`| `/mcsb`     | Manage your mcMMO Scoreboard.                       | `mcmmo.commands.mcscoreboard` |

---

## Admin Commands

Commands intended for server administrators to manage mcMMO settings and users.

| Command              | Aliases             | Description                                                    | Permission                      |
|----------------------|---------------------|----------------------------------------------------------------|---------------------------------|
| `/mmoedit`   | None      | Edit the mcMMO skill values for a user.   | `mcmmo.commands.mmoedit` |
| `/xprate`            | `/mcxprate`         | Modify the XP rate or start an event.                          | `mcmmo.commands.xprate`         |
| `/mcpurge`           | None                | Purge users with 0 power level and/or inactive for months.     | `mcmmo.commands.mcpurge`        |
| `/mcremove`          | None                | Remove a user from the mcMMO database.                         | `mcmmo.commands.mcremove`       |
| `/mcgod`             | None                | Toggle mcMMO god-mode on/off.                                  | `mcmmo.commands.mcgod`          |
| `/mcmmoreloadlocale` | `/mcreloadlocale`   | Reloads mcMMO locale settings.                                 | `mcmmo.commands.reloadlocale`   |
| `/mmoxpbar`          | `/xpbarsettings`    | Change XP bar settings.                                        | `mcmmo.commands.mmoxpbar`       |
| `/mcchatspy`         | None                | Toggle mcMMO Party Chat spying on/off.                        | `mcmmo.commands.mcchatspy`      |
| `/mcrefresh` | None      | Refresh all cooldowns for mcMMO abilities. | `mcmmo.commands.mcrefresh` |
| `/addxp`     | None                           | Adds mcMMO XP to a user.                  | `mcmmo.commands.addxp`    |
| `/addlevels` | None                           | Adds mcMMO levels to a user.              | `mcmmo.commands.addlevels`|
| `/skillreset`| None                           | Resets the level of one or all of your skills. | `mcmmo.commands.skillreset` |
| `/mcconvert` | None                           | Converts between different database and formula types. | `mcmmo.commands.mcconvert` |
| `/mcmmoreloadlocale` | `/mcreloadlocale`                                                                                            | Reloads mcMMO locale settings.          | `mcmmo.commands.reloadlocale` |

---

## Miscellaneous Commands

Additional commands for various functionalities within mcMMO.

| Command              | Aliases                                                                                                      | Description                             | Permission                    |
|----------------------|--------------------------------------------------------------------------------------------------------------|-----------------------------------------|-------------------------------|
| `/mcnotify`          | `/notify`                                                                                                    | Toggle mcMMO abilities chat display notifications on/off. | `mcmmo.commands.mcnotify`     |
| `/mcscoreboard`      | `/mcsb`                                                                                                      | Manage your mcMMO Scoreboard.           | `mcmmo.commands.mcscoreboard` |
| `/mcability`         | None                | Toggle whether abilities get readied on right-click.           | `mcmmo.commands.mcability`      |
| `/mmocompat` | None      | Provides information about server compatibility and mode. | None             |

## Removed Commands
These commands existed for a brief period of time in older versions of mcMMO.

| Command    | Aliases                                                                                                      | Description                                 | Permission                  |
|------------|--------------------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------|
| `/hardcore`| `/mchardcore`                                                                                                | Modify the mcMMO hardcore percentage or toggle hardcore mode (removed). | `mcmmo.commands.hardcore`       |
| `/vampirism`| `/mcvampirism`                                                                                               | Modify the mcMMO vampirism percentage or toggle vampirism mode (removed). | `mcmmo.commands.vampirism`      |
| `/mcfools` | `/macho`, `/jumping`, `/throwing`, `/wrecking`, `/walking`, `/swimming`, `/falling`, `/climbing`, `/flying`, `/diving`, `/piggy` | April Fools command (removed). | `mcmmo.commands.mcfools` |

