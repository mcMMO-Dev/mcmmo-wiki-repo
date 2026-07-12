---
title: persistent_data.yml
description: NBT persistence flags for mcMMO mob tracking.
published: true
date: 2026-07-12T00:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# persistent_data.yml

`persistent_data.yml` controls which mcMMO mob-tracking flags are persisted to disk (NBT data written when a chunk unloads) versus kept in memory only. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/persistent_data.yml).

> Changes require a full server restart.
{.is-warning}

---

## Why This Matters

mcMMO tags certain mobs with metadata to prevent XP exploits (e.g., a mob that came from a spawner should give 0 XP). When a mob's flag is **not** saved to disk (`Saved_To_Disk: false`), the flag lives only in memory; if the server restarts or the chunk unloads, the mob "forgets" its tag.

Enabling persistence (`Saved_To_Disk: true`) solves this but adds a small disk I/O cost every time a chunk containing that type of entity is unloaded. Servers with very large numbers of a given entity type (especially endermen or spawner mobs) should monitor TPS before enabling persistence for those categories.

---

## Mob Flags

Each flag is toggled by a `Saved_To_Disk` boolean nested under `Persistent_Data.Mobs.Flags.<FLAG>`. For example, spawner-mob persistence is set at `Persistent_Data.Mobs.Flags.MOB_SPAWNER_MOB.Saved_To_Disk`.

| Flag | Default | Description |
|------|---------|-------------|
| `MOB_SPAWNER_MOB` | `false` | Mobs that spawned from a mob spawner. Gives 0 XP by default. |
| `EGG_MOB` | `false` | Mobs spawned from spawn eggs. Gives 0 XP by default. |
| `NETHER_PORTAL_MOB` | `false` | Mobs that entered via a nether portal. Gives 0 XP by default. |
| `COTW_SUMMONED_MOB` | `true` | Pets summoned by Call of the Wild. Persistent by default because there are rarely many of them. |
| `PLAYER_BRED_MOB` | `false` | Mobs bred by players. Gives normal XP by default; adjust in `experience.yml`. |
| `EXPLOITED_ENDERMEN` | `false` | Endermen that arrived via the Enderman/Endermite exploit. Gives 0 XP. |
| `PLAYER_TAMED_MOB` | `false` | Mobs tamed by players. Gives 0 XP by default; adjust the multiplier at `Experience_Formula.Player_Tamed.Multiplier` in `experience.yml`. |

---

## mcMMO Region System

| Key | Default | Description |
|-----|---------|-------------|
| `mcMMO_Region_System.Enabled` | `true` | Track which blocks were placed by players. Disabling this enables XP exploits such as player-placed block duplication farms. **Do not disable.** |

The region system uses its own highly optimised file system separate from Spigot's NBT API, so it carries negligible performance cost.
