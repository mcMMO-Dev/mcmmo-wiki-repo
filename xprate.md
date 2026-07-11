---
title: XP Rate Events
description: Show or change XP rates and run server-wide XP events with /xprate.
published: true
date: 2026-07-11T00:00:00.000Z
tags: commands, experience
editor: markdown
dateCreated: 2026-07-11T00:00:00.000Z
---

# XP Rate Events

`/xprate` (alias `/mcxprate`) shows and changes mcMMO's XP rate multipliers, globally or for a single skill, and runs server-wide XP rate events. A rate multiplies all XP earned in the affected skills — `2` doubles XP gains, `1.5` grants 50% more.

```
/xprate
/xprate show
/xprate <rate> [true|false]
/xprate <skill|all> <rate> [true|false]
/xprate reset
```

> Rates changed with `/xprate` last until the server restarts or mcMMO's configs are reloaded — they are never written to `experience.yml`. For a permanent XP rate, set `Experience_Formula.Multiplier.Global` in `experience.yml` instead.
{.is-info}

## Examples

| Command | What it does |
|---------|--------------|
| `/xprate` | Shows the current XP rates and how long each has been active. |
| `/xprate show` | Same as `/xprate`. |
| `/xprate 2` | Starts an XP event with double XP for every skill. |
| `/xprate 1.5` | Starts an XP event with 50% bonus XP; decimal rates are supported. |
| `/xprate all 3` | Same as `/xprate 3` — `all` targets the global rate. |
| `/xprate mining 3` | Starts an XP event with triple Mining XP; other skills keep their current rates. |
| `/xprate fishing 2.5` | Starts an XP event with 2.5x Fishing XP. |
| `/xprate 2 false` | Doubles the global XP rate quietly, without the event fanfare. |
| `/xprate herbalism 4 false` | Sets a quiet 4x Herbalism rate without starting or ending an event. |
| `/xprate reset` | Ends the event and restores the rates configured in `experience.yml`. |
| `/xprate clear` | Same as `/xprate reset`. |

## Viewing the current rates

`/xprate` with no arguments (or `/xprate show`) lists the global rate and any per-skill rates, along with how long each modified rate has been active:

```
The current global XP rate is 2x (active for 2d 4h)
The current Mining XP rate is 5x (active for 45m 12s)
```

When every rate is at its configured value and no event is running, it reports `No XP rate event is active.` The `mcmmo.commands.xprate.show` permission is granted by default, so regular players can check the rates too.

The global rate is also available to PlaceholderAPI as `%mcmmo_xprate%` — see [Placeholders](/placeholders).

## XP events

Setting a rate normally starts an XP rate event:

- A `mcMMO Event!` banner and the new rate are broadcast in chat.
- A title is shown to all online players.
- Players who join during the event are told the global rate and any per-skill rates.

Per-skill events work the same way — `/xprate mining 3` announces the new Mining rate server-wide.

`/xprate reset` (or `/xprate clear`) ends the event with a `mcMMO Event Over!` broadcast, restores the global rate configured in `experience.yml`, and removes every per-skill rate.

Each of these announcements can be turned off — see the configuration table below.

## Quiet rate changes

Add `false` as the last argument to change a rate without the event fanfare:

```
/xprate 3 false
/xprate mining 2 false
```

The new rate is still announced in chat as a single line, but no event banner or titles are shown. `true` and `false` also accept `on`/`off` and `enabled`/`disabled`.

A quiet per-skill change never starts or ends an event, so you can adjust one skill's rate mid-event without disturbing it. If the quiet rate is lower than the rate of an ongoing global event, the announcement adds that the higher global rate still applies to that skill. A quiet global change, on the other hand, also quietly ends any running event — the rates stay in place, but join notices stop until a new event is started.

## How rates combine

- Per-skill rates never stack with the global rate — whichever is higher wins.
- Setting a global rate clears every per-skill rate at or below it, since those rates could never apply again; the command lists the skills it cleared.
- Rates below the configured baseline (`Experience_Formula.Multiplier.Global` in `experience.yml`) are rejected — `/xprate` raises rates above your configuration, it never lowers them below it. Use `/xprate reset` to return to the configured rates.
- The child skills Salvage and Smelting cannot have their own rate; they gain XP through their parent skills.

## Permissions

| Permission | Grants | Default |
|------------|--------|---------|
| `mcmmo.commands.xprate.show` | View the current rates with `/xprate` and `/xprate show` | Everyone |
| `mcmmo.commands.xprate.set` | Set global and per-skill rates and start events | Operators |
| `mcmmo.commands.xprate.reset` | Reset rates and end events with `/xprate reset` | Operators |
| `mcmmo.commands.xprate.all` | All of the above | Operators |

## Related configuration

| Setting | File | Default | Effect |
|---------|------|---------|--------|
| `Experience_Formula.Multiplier.Global` | `experience.yml` | `1.0` | The baseline global XP rate. `/xprate reset` restores it, and rates below it are rejected. |
| `General.EventBroadcasts` | `config.yml` | `true` | Chat announcements for rate changes and event starts and ends. |
| `General.EventInfoOnPlayerJoin` | `config.yml` | `true` | Tells joining players the active rates during an XP event. |
| `Feedback.Events.XP.SendTitles` | `advanced.yml` | `true` | Shows titles when an event starts or ends. |
