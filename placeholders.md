---
title: PlaceholderAPI Placeholders
description: List of supported placeholders.
published: true
date: 2026-07-12T00:00:00.000Z
tags: 
editor: markdown
dateCreated: 2025-11-19T20:46:03.114Z
---

# PlaceholderAPI

The plugin supports various different PlaceholderAPIs built in to the plugin! You do not need to install anything else to use these, just the plugin.

Placeholders work anywhere PlaceholderAPI does: chat formats, scoreboards, holograms, tab lists, menus, and more. To test any placeholder in game, use PlaceholderAPI's parse command:

```
/papi parse me %mcmmo_level_mining%
```

## Each Skill

Each skill has the following placeholders. Replace `<skillname>` with the lowercase name of the skill (e.g., `mining`, `fishing`).

The 19 skills are: `acrobatics`, `alchemy`, `archery`, `axes`, `crossbows`, `excavation`, `fishing`, `herbalism`, `maces`, `mining`, `repair`, `salvage`, `smelting`, `spears`, `swords`, `taming`, `tridents`, `unarmed`, `woodcutting`

| Placeholder | Returns | Example |
|-------------|---------|---------|
| `%mcmmo_level_<skillname>%` | The player's level in the skill | `%mcmmo_level_mining%` returns `847` |
| `%mcmmo_xp_<skillname>%` | XP earned toward the next level | `%mcmmo_xp_mining%` returns `2130` |
| `%mcmmo_xp_needed_<skillname>%` | Total XP the next level requires | `%mcmmo_xp_needed_mining%` returns `8570` |
| `%mcmmo_xp_remaining_<skillname>%` | XP still missing for the next level | `%mcmmo_xp_remaining_mining%` returns `6440` |
| `%mcmmo_rank_<skillname>%` | The player's position on the skill's leaderboard | `%mcmmo_rank_mining%` returns `12` |
| `%mcmmo_xprate_<skillname>%` | The player's XP perk multiplier for the skill (`1.0` without XP perks) | `%mcmmo_xprate_mining%` returns `1.5` |
| `%mcmmo_skillname_<skillname>%` | The skill's localized name as shown in messages | `%mcmmo_skillname_mining%` returns `Mining` |
| `%mcmmo_skillname_header_<skillname>%` | The skill's localized header name, as shown on skill command screens | `%mcmmo_skillname_header_mining%` returns `MINING` |

The two skill name placeholders follow the server's locale and any locale overrides, so renamed skills show their renamed values.

## Leaderboards

Leaderboard placeholders return entries from the same leaderboards as `/mctop`. Replace `<skillname>` as above and `<position>` with the leaderboard position you want. The child skills Salvage and Smelting have no leaderboard, so `mctop` placeholders are not available for them:

| Placeholder | Returns | Example |
|-------------|---------|---------|
| `%mcmmo_mctop_<skillname>:<position>%` | The skill level held by that leaderboard position | `%mcmmo_mctop_mining:1%` returns `1523` |
| `%mcmmo_mctop_name_<skillname>:<position>%` | The player name at that position | `%mcmmo_mctop_name_mining:1%` returns `Steve` |

Use `powerlevel`, `overall`, or `all` in place of the skill name for the power level leaderboard, e.g. `%mcmmo_mctop_powerlevel:25%`.

A top-3 display for a hologram or scoreboard looks like this:

```
#1 %mcmmo_mctop_name_mining:1% (%mcmmo_mctop_mining:1%)
#2 %mcmmo_mctop_name_mining:2% (%mcmmo_mctop_mining:2%)
#3 %mcmmo_mctop_name_mining:3% (%mcmmo_mctop_mining:3%)
```

and renders like this:

```
#1 Steve (1523)
#2 Alex (1449)
#3 Momshroom (1387)
```

Positions above `General.PlaceholderAPI.Leaderboards.Max_Tracked_Rank` in config.yml (100 by default), invalid positions, and positions no player currently holds return an empty result. Results come from a cache that refreshes on a schedule set by `General.Leaderboards.Refresh_Interval_Seconds.SQL` (default 60 seconds) for SQL storage or `General.Leaderboards.Refresh_Interval_Seconds.FlatFile` (default 600 seconds) for flat-file storage; see [config.yml](/config/config).

## Misc

As for everything else:

| Placeholder | Returns | Example |
|-------------|---------|---------|
| `%mcmmo_power_level%` | The player's power level | `2140` |
| `%mcmmo_power_level_cap%` | The configured power level cap | `10000` |
| `%mcmmo_in_party%` | Whether the player is in a party | `true` |
| `%mcmmo_party_name%` | The name of the player's party | `MushroomKingdom` |
| `%mcmmo_is_party_leader%` | Whether the player leads their party | `false` |
| `%mcmmo_party_leader%` | The name of the party leader | `Steve` |
| `%mcmmo_party_size%` | The number of members in the party | `4` |
| `%mcmmo_is_xp_event_active%` | Whether an XP rate event is running | `false` |
| `%mcmmo_xprate%` | The global XP rate multiplier, including an active XP rate event | `2.0` |
