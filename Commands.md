---
title: Commands
description: mcMMO commands
published: true
date: 2026-07-11T00:00:00.000Z
tags: commands
editor: markdown
dateCreated: 2024-11-24T01:51:14.196Z
---

# mcMMO Commands

## Plugin Info / Description

These commands provide basic information and settings for mcMMO.

| Command      | Aliases   | Description                              | Permission               |
|--------------|-----------|------------------------------------------|--------------------------|
| `/mcmmo`     | None      | Shows a brief description of mcMMO.      | `mcmmo.commands.mcmmo`   |

---

## Skill Management

Manage and view your mcMMO skills, experience, and rankings.

| Command      | Aliases                        | Description                              | Permission                |
|--------------|--------------------------------|------------------------------------------|---------------------------|
| `/mcrank`    | None                           | Displays your mcMMO ranking.             | `mcmmo.commands.mcrank`   |
| `/mcstats`   | `/stats`                       | Shows your mcMMO stats and XP.           | `mcmmo.commands.mcstats`  |
| `/mctop`     | None                           | Shows mcMMO leaderboards.                | `mcmmo.commands.mctop`    |
| `/mmopower`  | `/mmopowerlevel`, `/powerlevel`| (WIP) Shows your powerlevel. | `mcmmo.commands.mmopower` |

### Skill Commands

View detailed information about specific skills:

| Command        | Aliases | Description                           | Permission                   |
|----------------|---------|---------------------------------------|------------------------------|
| `/acrobatics`  | None    | Detailed mcMMO Acrobatics skill info. | `mcmmo.commands.acrobatics`  |
| `/alchemy`     | None    | Detailed mcMMO Alchemy skill info.    | `mcmmo.commands.alchemy`     |
| `/archery`     | None    | Detailed mcMMO Archery skill info.    | `mcmmo.commands.archery`     |
| `/axes`        | None    | Detailed mcMMO Axes skill info.       | `mcmmo.commands.axes`        |
| `/crossbows`   | None    | Detailed mcMMO Crossbows skill info.  | `mcmmo.commands.crossbows`   |
| `/excavation`  | None    | Detailed mcMMO Excavation skill info. | `mcmmo.commands.excavation`  |
| `/fishing`     | None    | Detailed mcMMO Fishing skill info.    | `mcmmo.commands.fishing`     |
| `/herbalism`   | None    | Detailed mcMMO Herbalism skill info.  | `mcmmo.commands.herbalism`   |
| `/maces`       | None    | Detailed mcMMO Maces skill info.      | `mcmmo.commands.maces`       |
| `/mining`      | None    | Detailed mcMMO Mining skill info.     | `mcmmo.commands.mining`      |
| `/repair`      | None    | Detailed mcMMO Repair skill info.     | `mcmmo.commands.repair`      |
| `/salvage`     | None    | Detailed mcMMO Salvage skill info.    | `mcmmo.commands.salvage`     |
| `/smelting`    | None    | Detailed mcMMO Smelting skill info.   | `mcmmo.commands.smelting`    |
| `/spears`      | None    | Detailed mcMMO Spears skill info.     | `mcmmo.commands.spears`      |
| `/swords`      | None    | Detailed mcMMO Swords skill info.     | `mcmmo.commands.swords`      |
| `/taming`      | None    | Detailed mcMMO Taming skill info.     | `mcmmo.commands.taming`      |
| `/tridents`    | None    | Detailed mcMMO Tridents skill info.   | `mcmmo.commands.tridents`    |
| `/unarmed`     | None    | Detailed mcMMO Unarmed skill info.    | `mcmmo.commands.unarmed`     |
| `/woodcutting` | None    | Detailed mcMMO Woodcutting skill info.| `mcmmo.commands.woodcutting` |

---

## Party Commands

Manage your party and interact with party members.

| Command     | Aliases      | Description                                    | Permission                 |
|-------------|--------------|------------------------------------------------|----------------------------|
| `/party`    | None         | Create or join a party.                        | `mcmmo.commands.party`     |
| `/partychat`| `/pc`, `/p`  | Toggle party chat or send party chat messages. | `mcmmo.chat.partychat`     |
| `/ptp`      | None         | Teleport to a party member.                    | `mcmmo.commands.ptp`       |

---

## Admin Chat Commands

Manage chat-related functionalities within mcMMO.

| Command        | Aliases     | Description                                         | Permission                  |
|----------------|-------------|-----------------------------------------------------|-----------------------------|
| `/adminchat`   | `/ac`, `/a` | Toggle Admin chat or send admin chat messages.      | `mcmmo.chat.adminchat`      |

---

## Admin Commands

Commands intended for server administrators to manage mcMMO settings and users.

| Command              | Aliases           | Description                                                    | Permission                    |
|----------------------|-------------------|----------------------------------------------------------------|-------------------------------|
| `/addlevels`         | None              | Adds mcMMO levels to a user.                                   | `mcmmo.commands.addlevels`    |
| `/addxp`             | None              | Adds mcMMO XP to a user.                                       | `mcmmo.commands.addxp`        |
| `/inspect`           | None              | Inspect another player's mcMMO stats.                          | `mcmmo.commands.inspect`      |
| `/mcchatspy`         | None              | Toggle mcMMO Party Chat spying on/off.                         | `mcmmo.commands.mcchatspy`    |
| `/mcconvert`         | None              | Converts between different database and formula types.         | `mcmmo.commands.mcconvert`    |
| `/mccooldown`        | None              | Shows remaining cooldowns for mcMMO abilities.                 | `mcmmo.commands.mccooldown`   |
| `/mcgod`             | None              | Toggle mcMMO god-mode on/off.                                  | `mcmmo.commands.mcgod`        |
| `/mcmmoreloadlocale` | `/mcreloadlocale` | Reloads mcMMO locale settings.                                 | `mcmmo.commands.reloadlocale` |
| `/mcpurge`           | None              | Purge users with 0 power level and/or inactive for months.     | `mcmmo.commands.mcpurge`      |
| `/mcrefresh`         | None              | Refresh all cooldowns for mcMMO abilities.                     | `mcmmo.commands.mcrefresh`    |
| `/mcremove`          | None              | Remove a user from the mcMMO database.                         | `mcmmo.commands.mcremove`     |
| `/mmodebug`          | None              | Displays debug information for mcMMO.                          | `mcmmo.commands.mmodebug`     |
| `/mmoedit`           | None              | Edit the mcMMO skill values for a user.                        | `mcmmo.commands.mmoedit`      |
| `/mmoinfo`           | None              | Displays version and server info for mcMMO.                    | `mcmmo.commands.mmoinfo`      |
| `/mmoshowdb`         | None              | Shows the current database type being used by mcMMO.           | `mcmmo.commands.mmoshowdb`    |
| `/mmoxpbar`          | `/xpbarsettings`  | Change XP bar settings.                                        | `mcmmo.commands.mmoxpbar`     |
| `/skillreset`        | None              | Resets the level of one or all of your skills.                 | `mcmmo.commands.skillreset`   |
| `/xprate`            | `/mcxprate`       | Show or modify the XP rate, globally or for a single skill, or start an XP event. | `mcmmo.commands.xprate`       |

`/addxp`, `/addlevels`, and `/mmoedit` accept `-s` as the last argument to run silently, suppressing the messages they would otherwise send.

---

## Miscellaneous Commands

Additional commands for various functionalities within mcMMO.

| Command         | Aliases   | Description                                               | Permission                    |
|-----------------|-----------|-----------------------------------------------------------|-------------------------------|
| `/mcability`    | None      | Toggle whether abilities get readied on right-click.      | `mcmmo.commands.mcability`    |
| `/mclevelupsound` | `/levelupsound` | Toggle the mcMMO level-up sound on/off.           | `mcmmo.commands.mclevelupsound` |
| `/mcnotify`     | `/notify` | Toggle mcMMO abilities chat display notifications on/off. | `mcmmo.commands.mcnotify`     |
| `/mcscoreboard` | `/mcsb`   | Manage your mcMMO Scoreboard.                             | `mcmmo.commands.mcscoreboard` |

## Removed Commands
These commands existed for a brief period of time in older versions of mcMMO.

| Command      | Aliases                                                                                                      | Description                                 | Permission                        |
|--------------|--------------------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|-
| `/hardcore`  | `/mchardcore`                                                                                                | Modify the mcMMO hardcore percentage or toggle hardcore mode (removed). | `mcmmo.commands.hardcore` |
| `/mcfools`   | `/macho`, `/jumping`, `/throwing`, `/wrecking`, `/walking`, `/swimming`, `/falling`, `/climbing`, `/flying`, `/diving`, `/piggy` | April Fools command (removed). | `mcmmo.commands.mcfools` |
| `/mmocompat` | None                                                                                                         | Provided information about server compatibility and mode (removed). | None |
| `/vampirism` | `/mcvampirism`                                                                                               | Modify the mcMMO vampirism percentage or toggle vampirism mode (removed). | `mcmmo.commands.vampirism` |

