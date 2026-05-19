---
title: config.yml
description: Main mcMMO configuration reference.
published: true
date: 2026-05-17T00:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# config.yml

`config.yml` is the main configuration file for mcMMO. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/config.yml).

> All changes to `config.yml` require a full server restart. Reloading is **not** supported.
{.is-warning}

---

## General

| Key | Default | Description |
|-----|---------|-------------|
| `General.RetroMode.Enabled` | `true` | Scales mcMMO to 0–1000 skill levels (10× multiplier on all level requirements). Pure cosmetic — the underlying math is identical to Standard mode. |
| `General.Locale` | `en_US` | Locale file to use for all mcMMO messages. See [Locale](/locale). |
| `General.MOTD_Enabled` | `true` | Show an mcMMO message of the day when players join. |
| `General.AdminNotifications` | `true` | Send admin-level notices (e.g. config warnings) to operators. |
| `General.Show_Profile_Loaded` | `false` | Send a chat message to the player when their profile is loaded from the database. |
| `General.Save_Interval` | `10` | Minutes between automatic saves of player data. |
| `General.Power_Level_Cap` | `0` | Maximum allowed power level (sum of all skills). `0` = no cap. |
| `General.TruncateSkills` | `true` | If you lower a skill's `Level_Cap`, this trims any levels above the new cap. |
| `General.Verbose_Logging` | `false` | Print detailed debug output to the console. |
| `General.Config_Update_Overwrite` | `true` | When mcMMO adds new config keys after an update, overwrite the existing config. Set to `false` to write a `.new` file alongside instead. |
| `General.Refresh_Chunks` | `false` | Refresh chunks around a player when a super ability ends (fixes client-side block glitches). Resource-intensive on large servers. |

### Level-Up Broadcasts

`General.Level_Up_Chat_Broadcasts` controls whether the server announces level milestones in chat.

| Key | Default | Description |
|-----|---------|-------------|
| `Enabled` | `true` | Broadcast skill level milestones. |
| `Milestone_Interval` | `100` | Broadcast every N levels. `1` = every level, `100` = every 100 levels. |
| `Broadcast_Powerlevels.Enabled` | `true` | Also broadcast power level milestones. |
| `Broadcast_Targets.Only_Party_Members` | `false` | Restrict broadcasts to party members only. |
| `Broadcast_Targets.Only_Same_World` | `false` | Only send to players in the same world. |
| `Distance_Restrictions.Restrict_Distance` | `false` | Limit broadcast range. |
| `Distance_Restrictions.Restricted_Radius` | `100` | Broadcast radius in blocks (only when restriction is on). |

---

## Scoreboard

mcMMO can display stats in the Minecraft sidebar scoreboard.

| Key | Default | Description |
|-----|---------|-------------|
| `Scoreboard.UseScoreboards` | `false` | Master toggle for scoreboard display. |
| `Scoreboard.Power_Level_Tags` | `false` | Display players' power levels below their names. |
| `Scoreboard.Allow_Keep` | `true` | Allow players to pin the scoreboard with `/mcscoreboard keep`. |
| `Scoreboard.Show_Stats_After_Login` | `false` | Automatically show `/mcstats` scoreboard on login. |
| `Scoreboard.Tips_Amount` | `5` | How many times to show scoreboard usage tips per session. `0` = never. |

Each command type (`Rank`, `Top`, `Stats`, `Inspect`, `Cooldown`, `Skill`) has its own `Print` (chat output), `Board` (sidebar), and `Display_Time` (seconds before clearing, `-1` = permanent) settings.

---

## Mob Health Bar

| Key | Default | Description |
|-----|---------|-------------|
| `Mob_Healthbar.Enabled` | `true` | Show a health bar above mobs when hit. |
| `Mob_Healthbar.Display_Type` | `HEARTS` | Default display style: `HEARTS`, `BAR`, or `DISABLED`. Players can override with `/mcmmo`.  |
| `Mob_Healthbar.Display_Time` | `3` | Seconds to display the health bar. |

---

## Database Purging

| Key | Default | Description |
|-----|---------|-------------|
| `Database_Purging.Purge_Interval` | `-1` | Hours between purge runs. `0` = on startup only, `-1` = never. |
| `Database_Purging.Old_User_Cutoff` | `6` | Remove players who haven't connected in this many months. `-1` = never purge. |

---

## Backups

mcMMO can zip config and flatfile data on shutdown.

| Key | Default | Description |
|-----|---------|-------------|
| `Backups.Enabled` | `true` | Enable automatic backups. |
| `Backups.Keep.Last_24_Hours` | `true` | Keep one backup per hour for the last 24 hours. |
| `Backups.Keep.Daily_Last_Week` | `true` | Keep one backup per day for the last week. |
| `Backups.Keep.Weekly_Past_Months` | `true` | Keep one backup per week beyond that. |

---

## MySQL

By default mcMMO uses a flat-file database. To use MySQL instead:

| Key | Default | Description |
|-----|---------|-------------|
| `MySQL.Enabled` | `false` | Enable MySQL storage. |
| `MySQL.Database.User_Name` | `UserName` | MySQL username. |
| `MySQL.Database.User_Password` | `UserPassword` | MySQL password. |
| `MySQL.Database.Name` | `DataBaseName` | Database name. |
| `MySQL.Database.TablePrefix` | `mcmmo_` | Prefix for all mcMMO tables. |
| `MySQL.Database.MaxConnections.Misc/Load/Save` | `30/30/30` | Max simultaneous connections per pool. |
| `MySQL.Database.MaxPoolSize.Misc/Load/Save` | `10/20/20` | Cached connection pool size. |
| `MySQL.Server.Port` | `3306` | MySQL server port. |
| `MySQL.Server.Address` | `localhost` | MySQL server address. |
| `MySQL.Server.SSL` | `true` | Use SSL for MySQL connections. |

---

## Hardcore Mode & Vampirism

Configured here but documented on their own pages:
- [Hardcore Mode](/config/hardcore-mode) — death penalty (lose skill levels on death).
- [Vampirism](/config/vampirism) — PvP skill stealing.

---

## Mods (Custom Items)

| Key | Default | Description |
|-----|---------|-------------|
| `Mods.Tool_Mods_Enabled` | `false` | Enable custom modded tools (e.g. from mods) to interact with mcMMO skills. |
| `Mods.Armor_Mods_Enabled` | `false` | Enable custom modded armour. |
| `Mods.Block_Mods_Enabled` | `false` | Enable custom modded blocks. |
| `Mods.Entity_Mods_Enabled` | `false` | Enable custom modded entities. |

Custom item definitions go in separate `mods/` YAML files which mcMMO will read when this is enabled.

---

## Items

### Chimaera Wing

The Chimaera Wing is a consumable item that teleports the player to their bed or spawn.

| Key | Default | Description |
|-----|---------|-------------|
| `Items.Chimaera_Wing.Enabled` | `true` | Enable the Chimaera Wing item. |
| `Items.Chimaera_Wing.Cooldown` | `240` | Cooldown in seconds after use. |
| `Items.Chimaera_Wing.Warmup` | `5` | Seconds of casting time before teleport. |
| `Items.Chimaera_Wing.RecentlyHurt_Cooldown` | `60` | Seconds after taking damage before you can use it. |
| `Items.Chimaera_Wing.Prevent_Use_Underground` | `true` | Block use when the player is underground. |
| `Items.Chimaera_Wing.Use_Bed_Spawn` | `true` | Prefer the player's bed/respawn anchor over world spawn. |
| `Items.Chimaera_Wing.Use_Cost` | `1` | Number of feathers consumed per use. |
| `Items.Chimaera_Wing.Recipe_Cost` | `5` | Number of feathers in the crafting recipe. |
| `Items.Chimaera_Wing.Item_Name` | `FEATHER` | Material that acts as the Chimaera Wing. |

---

## Parties

| Key | Default | Description |
|-----|---------|-------------|
| `Party.FriendlyFire` | `false` | Allow players to damage their own party members. |
| `Party.MaxSize` | `-1` | Maximum party size. `-1` = unlimited. |
| `Party.AutoKick_Interval` | `12` | Hours between auto-kick checks for inactive members. `0` = on startup, `-1` = never. |
| `Party.Old_Party_Member_Cutoff` | `7` | Kick members not seen in this many days. |
| `Party.Sharing.ExpShare_bonus_base` | `1.1` | Base XP multiplier for party XP sharing. |
| `Party.Sharing.ExpShare_bonus_increase` | `1.05` | Per-member bonus multiplier increase. |
| `Party.Sharing.ExpShare_bonus_cap` | `1.5` | Maximum XP sharing multiplier. |
| `Party.Sharing.Range` | `75.0` | Distance in blocks within which XP sharing applies. |

### Party Leveling

Parties have their own level that unlocks features:

| Key | Default | Unlock |
|-----|---------|--------|
| `Chat_UnlockLevel` | `1` | Party chat |
| `Teleport_UnlockLevel` | `2` | `/ptp` party teleport |
| `Alliance_UnlockLevel` | `5` | Party alliances |
| `ItemShare_UnlockLevel` | `8` | Item sharing |
| `XpShare_UnlockLevel` | `10` | XP sharing |
| `Leveling.Level_Cap` | `10` | Maximum party level |

---

## Abilities (Super Abilities)

| Key | Default | Description |
|-----|---------|-------------|
| `Abilities.Enabled` | `true` | Master toggle for all super abilities. |
| `Abilities.Messages` | `true` | Send activation/deactivation messages. |
| `Abilities.Activation.Only_Activate_When_Sneaking` | `false` | Require sneaking to ready a tool for ability activation. |

**Cooldowns (seconds):**

| Ability | Default |
|---------|---------|
| Berserk | 240 |
| Blast Mining | 60 |
| Giga Drill Breaker | 240 |
| Green Terra | 240 |
| Serrated Strikes | 240 |
| Skull Splitter | 240 |
| Super Breaker | 240 |
| Tree Feller | 240 |

`Max_Seconds` for each ability defaults to `0` (no cap beyond the level-based formula). Setting a positive value caps the duration regardless of level.

`Abilities.Limits.Tree_Feller_Threshold` (default `1000`) caps the number of blocks Tree Feller will break per activation.

`Abilities.Tools.Durability_Loss` (default `1`) sets extra durability damage per block broken while an ability is active. Set to `0` to disable extra wear.

---

## Per-Skill Settings

Each skill has a `Skills.<SkillName>` block. Common options:

| Key | Description |
|-----|-------------|
| `Level_Cap` | Maximum level for this skill. `0` = unlimited. |
| `Enabled_For_PVP` | Whether the skill's combat bonuses apply in PvP. |
| `Enabled_For_PVE` | Whether the skill's combat bonuses apply in PvE. |

Notable skill-specific settings:

### Fishing
| Key | Default | Description |
|-----|---------|-------------|
| `Drops_Enabled` | `true` | Enable Treasure Hunter drops. |
| `Override_Vanilla_Treasures` | `true` | Replace the vanilla fishing loot table with mcMMO's when Treasure Hunter procs. |
| `Extra_Fish` | `false` | Always grant a fish in addition to any treasure found. |
| `Lure_Modifier` | `4.0` | Multiplier applied to Luck of the Sea bonus for treasure drop chance. |

### Herbalism
| Key | Default | Description |
|-----|---------|-------------|
| `Prevent_AFK_Leveling` | `true` | Reduce XP when a player harvests the same block repeatedly in a short window (AFK farm detection). |

### Mining
| Key | Default | Description |
|-----|---------|-------------|
| `Detonator_Name` | `FLINT_AND_STEEL` | Item used to trigger Blast Mining. |

### Repair
| Key | Default | Description |
|-----|---------|-------------|
| `Anvil_Material` | `IRON_BLOCK` | Block that acts as the mcMMO repair anvil. |
| `Use_Enchanted_Materials` | `false` | Allow using enchanted items as repair material. |
| `Confirm_Required` | `true` | Require a second tap to confirm repairing enchanted items. |

### Salvage
| Key | Default | Description |
|-----|---------|-------------|
| `Anvil_Material` | `GOLD_BLOCK` | Block that acts as the mcMMO salvage anvil. |
| `Confirm_Required` | `true` | Require a second tap to confirm salvaging enchanted items. |

### Taming — Call of the Wild
Each pet type (Wolf, Ocelot, Horse) can be configured with the item needed to summon it, amount required, number summoned, duration, and per-player limit.

### Unarmed
| Key | Default | Description |
|-----|---------|-------------|
| `Block_Cracker.Allow_Block_Cracker` | `true` | Allow Berserk to crack mossy stone bricks into regular stone bricks. |
| `Items_As_Unarmed` | `false` | Treat any attack without a dedicated weapon (including holding a random block) as unarmed. |

---

## Bonus Drops (`Bonus_Drops`)

Lists every block that is eligible for mcMMO double/triple drop bonuses. `true` = eligible, `false` = excluded. Covers Herbalism, Mining, Woodcutting, and Smelting output items.

---

## Commands

| Key | Default | Description |
|-----|---------|-------------|
| `Commands.Skills.URL_Links` | `true` | Append a wiki URL when players run a skill command. |
| `Commands.Generic.Match_OfflinePlayers` | `false` | Match partial player names against offline players (can be slow with many offline players). |
| `Commands.Database.Player_Cooldown` | `1750` | Milliseconds between `/mctop` or `/mcrank` uses per player. |
| `Commands.inspect.Max_Distance` | `30.0` | Maximum distance to inspect another player. |
| `Commands.ptp.Cooldown` | `120` | Seconds between `/ptp` uses. |
| `Commands.ptp.Warmup` | `5` | Seconds of casting time before teleport. |
| `Commands.ptp.Accept_Required` | `true` | The target must `/ptpaccept` before the teleport occurs. |
| `Commands.ptp.Request_Timeout` | `300` | Seconds before a pending `/ptp` request expires. |
| `Commands.ptp.World_Based_Permissions` | `false` | Require `mcmmo.commands.ptp.world.<WorldName>` permission per world. |

---

## Green Thumb Auto-Replanting

`Green_Thumb_Replanting_Crops` lists which crop types Green Thumb will auto-replant after harvest. Set a crop to `false` to opt it out.
