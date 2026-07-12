---
title: level_up_commands.yml
description: Run commands when players reach chosen skill levels or power levels.
published: true
date: 2026-07-12T00:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-07-11T00:00:00.000Z
---

# level_up_commands.yml

`level_up_commands.yml` makes mcMMO run server commands when players reach chosen skill levels or power levels. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/level_up_commands.yml).

The shipped example entries are disabled; set `enabled: true` on an entry (or write your own) to use it.

> Changes require a full server restart.
{.is-warning}

---

## Entry structure

Every entry under `level_up_commands` needs `commands` plus at least one trigger. An entry may use both trigger types and fires when either one matches.

| Field | Description |
|-------|-------------|
| `skills` | Skill names to watch. Accepts a single name, a list, or `all` for every skill. Used together with `levels`. |
| `levels` | Skill levels that trigger the entry, for any of the listed skills. |
| `power_levels` | Power levels that trigger the entry. The power level is the sum of the player's skill levels, counting only skills they have permission for. |
| `commands` | The commands to run, without a leading slash. Accepts a single command or a list. |
| `enabled` | Set to `false` to keep an entry without it running. Defaults to `true`. |
| `run_as` | Who executes the commands: `CONSOLE` (default) or `PLAYER`. `PLAYER` runs the commands as the player, using their permissions. |

## Placeholders

Commands can include the following placeholders:

| Placeholder | Value |
|-------------|-------|
| `{@player}` | The player's name. |
| `{@skill}` | The localized name of the skill that leveled up (skill triggers only). |
| `{@level}` | The milestone level that was reached (skill triggers only). |
| `{@power_level}` | The milestone power level for `power_levels` triggers, otherwise the player's current power level. |
| `{@mining_level}` | The player's current level in that skill. Works for every non-child skill, e.g. `{@herbalism_level}`, `{@archery_level}`. The child skills Salvage and Smelting have no token, so `{@salvage_level}` and `{@smelting_level}` are left unchanged. |

When PlaceholderAPI is installed, PlaceholderAPI placeholders in commands are also resolved against the player who leveled up, including [mcMMO's own placeholders](/placeholders), e.g. `%player_world%` or `%mcmmo_power_level%`.

## Behavior

Commands run once per milestone reached, even when several levels are gained at once. A player jumping from level 8 to 12 with milestones at 10 and 12 triggers each milestone once.

Malformed entries are skipped with a console warning naming the entry, so one broken entry never stops the rest of the file from loading.

Color codes like `&6` are not translated inside commands; for styled messages use a JSON component command instead (see below).

## Example

```yaml
level_up_commands:
    mining_milestones:
        enabled: true
        skills: [ Mining, Excavation ]
        levels: [ 10, 50, 100 ]
        commands:
            - "say {@player} reached level {@level} in {@skill}!"
            - "give {@player} minecraft:diamond 1"
    power_level_milestones:
        enabled: true
        power_levels: [ 500, 1000, 2000 ]
        commands:
            - "say {@player} has reached power level {@power_level}!"
```

## JSON component messages

For colored, formatted, or hoverable messages, use vanilla `tellraw`, which takes a JSON chat component. `tellraw` also sends a system message, so it avoids the `[Not Secure]` console tag that `say` and `me` produce on modern Minecraft.

Minecraft 1.21.5 renamed the hover event keys and made JSON parsing strict, so the JSON differs by server version.

On Minecraft 1.21.5 and newer, use `hover_event` with `value`:

```yaml
fancy_message:
    skills: all
    levels: [ 250 ]
    commands:
        - 'tellraw {@player} {"text":"","extra":[{"text":"Milestone! ","color":"gold","bold":true},{"text":"[{@skill} {@level}]","color":"aqua","underlined":true,"hover_event":{"action":"show_text","value":"Keep it up, {@player}! Power level: {@power_level}"}},{"text":" (hover for details)","color":"gray","italic":true}]}'
```

On older versions, use `hoverEvent` with `contents`:

```yaml
fancy_message:
    skills: all
    levels: [ 250 ]
    commands:
        - 'tellraw {@player} {"text":"","extra":[{"text":"Milestone! ","color":"gold","bold":true},{"text":"[{@skill} {@level}]","color":"aqua","underlined":true,"hoverEvent":{"action":"show_text","contents":"Keep it up, {@player}! Power level: {@power_level}"}},{"text":" (hover for details)","color":"gray","italic":true}]}'
```

Both produce a gold "Milestone!" banner with an aqua, underlined skill tag that shows extra detail when hovered.

## For developers

Other plugins can register their own level up commands or callbacks through `LevelUpCommandAPI`. See the [API page](/api/mcmmo-api) for examples.
