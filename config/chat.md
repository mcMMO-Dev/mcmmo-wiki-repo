---
title: chat.yml
description: mcMMO chat channel configuration reference.
published: true
date: 2026-05-17T00:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# chat.yml

`chat.yml` controls mcMMO's built-in chat channels: party chat and admin chat. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/chat.yml).

> Changes require a full server restart.
{.is-warning}

---

## Settings

| Key | Default | Description |
|-----|---------|-------------|
| `Chat.Enable` | `true` | Master toggle for all mcMMO chat processing. Disabling this prevents party chat and admin chat from functioning. |

### Party Chat

| Key | Default | Description |
|-----|---------|-------------|
| `Chat.Channels.Party.Enable` | `true` | Enable the party chat channel (`/p`). |
| `Chat.Channels.Party.Use_Display_Names` | `true` | Show players' display names in party chat instead of their usernames. |
| `Chat.Channels.Party.Send_To_Console` | `true` | Log party chat messages to the server console. |
| `Chat.Channels.Party.Spies.Automatically_Enable_Spying` | `false` | Players with the chat spy permission will have spy mode on by default when they join. |

### Admin Chat

| Key | Default | Description |
|-----|---------|-------------|
| `Chat.Channels.Admin.Enable` | `true` | Enable the admin chat channel (`/a`). |
| `Chat.Channels.Admin.Use_Display_Names` | `true` | Show display names in admin chat. |
| `Chat.Channels.Admin.Send_To_Console` | `true` | Log admin chat messages to the console. |

---

## Customising Chat Appearance

The visual formatting of chat messages (prefix, colours, layout) is handled through the **locale** system, not through `chat.yml`.

To customise how party chat or admin chat looks, open your locale file and search for `chat` — the relevant locale keys are grouped there. See the [Locale](/locale) page for full details.
