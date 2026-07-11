---
title: sounds.yml
description: mcMMO sound event configuration reference.
published: true
date: 2026-07-11T00:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# sounds.yml

`sounds.yml` controls the volume, pitch, and optionally the sound ID of every sound mcMMO plays. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/sounds.yml).

> Changes require a full server restart.
{.is-warning}

---

## Master Volume

| Key | Default | Description |
|-----|---------|-------------|
| `Sounds.MasterVolume` | `1.0` | Global volume multiplier. `1.0` = max, `0.0` = silent. |

---

## Per-Sound Settings

Each sound event has three common fields:

| Field | Description |
|-------|-------------|
| `Enable` | Whether this sound plays at all. |
| `Volume` | Playback volume (0.0–1.0, or higher for greater range). |
| `Pitch` | Playback pitch (1.0 = normal). Lower = deeper, higher = sharper. |
| `CustomSoundId` | Optional Bukkit sound ID string (e.g. `minecraft:entity.player.levelup`). Leave blank (`''`) to use the default mcMMO sound. |

> `FIZZ` and `POP` do not have a `Pitch` field; their pitch is randomised on each play.
{.is-info}

---

## Sound Events

| Sound Key | Default Enabled | Notes |
|-----------|----------------|-------|
| `ITEM_CONSUMED` | `true` | Item is consumed (e.g. Chimaera Wing use). |
| `GLASS` | `true` | Generic glass break. |
| `ANVIL` | `true` | Repair/salvage anvil interaction. Pitch 0.3 (low thud). |
| `FIZZ` | `true` | Random pitch each time. |
| `LEVEL_UP` | `true` | Skill level-up jingle. |
| `ITEM_BREAK` | `true` | Item durability hits 0. |
| `POP` | `true` | Random pitch each time. |
| `CHIMAERA_WING` | `true` | Chimaera Wing teleport. |
| `ROLL_ACTIVATED` | `true` | Acrobatics Roll triggered. |
| `SKILL_UNLOCKED` | `true` | A new sub-skill rank becomes available. |
| `DEFLECT_ARROWS` | `true` | Arrow deflected (Unarmed). |
| `TOOL_READY` | `true` | Tool readied for super ability activation. |
| `ABILITY_ACTIVATED_GENERIC` | `true` | Generic super ability start. |
| `ABILITY_ACTIVATED_BERSERK` | `true` | Berserk specifically. |
| `TIRED` | `true` | Super ability expired (tool unreadied). |
| `BLEED` | `true` | Bleed proc (Swords). |
| `CRIPPLE` | `true` | Maces Cripple effect. The default sound is the mace smash ground sound, which exists on Minecraft 1.21 and newer. |

---

## Custom Sounds

To replace any sound with a custom or resource-pack sound, set `CustomSoundId` to a valid Bukkit sound identifier:

```yaml
LEVEL_UP:
    Enable: true
    Volume: 0.5
    Pitch: 1.0
    CustomSoundId: 'my_pack:custom.levelup'
```

The ID format is `namespace:path` matching your resource pack's `sounds.json`.

Sound IDs that cannot be resolved (for example a typo in `CustomSoundId`) log a single warning and are skipped.
