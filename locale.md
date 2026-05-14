---
title: Localization
description: Information about mcMMO's locale system, color codes, and tooltip customization.
published: true
date: 2026-05-14T00:00:00.000Z
tags: locale
editor: markdown
dateCreated: 2022-07-18T00:13:13.163Z
---

# Locale

mcMMO uses `.properties` locale files for all in-game text — messages, skill names, tooltips, colors, and formatting. Everything visible to players can be customized through the locale system.

## Built-in translations

mcMMO ships with translations for many languages. To switch languages, set `General.Locale` in `config.yml` to the appropriate locale code, then restart the server.

| Locale code | Language |
|-------------|----------|
| `en_US` | English (default) |
| `de` | German |
| `es` | Spanish |
| `fr` | French |
| `it` | Italian |
| `ja_JP` | Japanese |
| `ko` | Korean |
| `pl` | Polish |
| `pt_BR` | Portuguese (Brazil) |
| `ru` | Russian |
| `zh_CN` | Chinese (Simplified) |
| `zh_TW` | Chinese (Traditional) |

Full list: [GitHub locale folder](https://github.com/mcMMO-Dev/mcMMO/tree/master/src/main/resources/locale)

> Community translations are maintained by volunteers and may lag behind new features. Missing keys fall back to `en_US` automatically.
{.is-info}

## Locale override file

Rather than editing a locale inside the JAR, mcMMO generates an override file on startup:

```
plugins/mcMMO/locales/locale_override.properties
```

**How it works:**
1. mcMMO checks for `locale_override.properties` first.
2. Any key found there takes priority over the bundled locale.
3. Missing keys fall back to the active locale, then to `en_US`.

This means you only need to copy the keys you want to change — you don't need to copy the entire file. If mcMMO updates a key you haven't overridden, you'll get the update automatically.

> Copy only the keys you want to change. Copying the whole file means you'll miss future text updates unless you track them manually.
{.is-warning}

**Finding keys:**
The master key list is in `en_US`: [locale_en_US.properties on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/locale/locale_en_US.properties)

**Applying changes:**
- Restart the server, **or**
- Run `/mcmmoreloadlocale` (alias: `/mcreloadlocale`) — affects the locale file only, not config files. Requires the `mcmmo.commands.reloadlocale` permission.

---

## Color codes

mcMMO locale files support three color code formats. All three work everywhere in the locale.

### Format 1 — `&` codes (standard Minecraft)

The familiar `&` prefix followed by a single character:

| Code | Color/Format | Code | Color/Format |
|------|-------------|------|-------------|
| `&0` | Black | `&l` | **Bold** |
| `&1` | Dark Blue | `&n` | Underline |
| `&2` | Dark Green | `&o` | *Italic* |
| `&3` | Dark Aqua | `&m` | ~~Strikethrough~~ |
| `&4` | Dark Red | `&k` | Obfuscated |
| `&5` | Dark Purple | `&r` | Reset |
| `&6` | Gold | | |
| `&7` | Gray | | |
| `&8` | Dark Gray | | |
| `&9` | Blue | | |
| `&a` | Green | | |
| `&b` | Aqua | | |
| `&c` | Red | | |
| `&d` | Light Purple | | |
| `&e` | Yellow | | |
| `&f` | White | | |

**Example:**
```properties
mcMMO.Template.Prefix=&6(&amcMMO&6) &7{0}
```

---

### Format 2 — `[[NAME]]` tokens (mcMMO named colors)

mcMMO's own color token format. Useful when you want readable names in your locale file instead of codes.

| Token | Equivalent |
|-------|-----------|
| `[[BLACK]]` | `&0` |
| `[[DARK_BLUE]]` | `&1` |
| `[[DARK_GREEN]]` | `&2` |
| `[[DARK_AQUA]]` | `&3` |
| `[[DARK_RED]]` | `&4` |
| `[[DARK_PURPLE]]` | `&5` |
| `[[GOLD]]` | `&6` |
| `[[GRAY]]` | `&7` |
| `[[DARK_GRAY]]` | `&8` |
| `[[BLUE]]` | `&9` |
| `[[GREEN]]` | `&a` |
| `[[AQUA]]` | `&b` |
| `[[RED]]` | `&c` |
| `[[LIGHT_PURPLE]]` | `&d` |
| `[[YELLOW]]` | `&e` |
| `[[WHITE]]` | `&f` |
| `[[BOLD]]` | `&l` |
| `[[UNDERLINE]]` | `&n` |
| `[[ITALIC]]` | `&o` |
| `[[STRIKE]]` | `&m` |
| `[[MAGIC]]` | `&k` |
| `[[RESET]]` | `&r` |

**Example:**
```properties
Skills.Overhaul.Header=[[DARK_AQUA]][[BOLD]]{0}
```

---

### Format 3 — `&#RRGGBB` hex colors

Full 24-bit RGB color support. Use a standard web hex code prefixed with `&`:

```properties
My.Key=&#FF5500Orange text here
My.Key2=&#00FF88Some mint green text
```

Formats can be freely mixed in the same value:
```properties
My.Key=&lBold then &#FF0000red then &r reset
```

---

## JSON tooltip keys

mcMMO displays rich hover tooltips when players run skill commands (e.g. `/mining`). These tooltips are driven by `JSON.*` keys in the locale. Colors are set directly in the locale values using the same `&` codes and `&#RRGGBB` hex formats as any other key.

### Hex colors in JSON tooltip keys

Hex colors work in `JSON.*` keys using the same `&#RRGGBB` format as anywhere else in the locale:

```properties
JSON.Type.SuperAbility=&#FF55FFSuper Ability
JSON.Hover.SkillName=&#00FFAASkill Name Here
JSON.DescriptionHeader=&#AAAAFF&lDescription:
```

All three color formats are supported:

| Format | Example |
|--------|---------|
| `&` code | `&a&lPassive&r` |
| `[[NAME]]` token | `[[GREEN]][[BOLD]]Passive[[RESET]]` |
| Hex | `&#00FF00&lPassive&r` |

### Tooltip structure keys

| Key | Default value | Purpose |
|-----|--------------|---------|
| `JSON.DescriptionHeader` | `&5Description:` | Header above the sub-skill description |
| `JSON.Locked` | `&8-=[LOCKED]=-` | Shown for sub-skills the player hasn't unlocked yet |
| `JSON.LevelRequirement` | `&9Level Requirement` | Label for unlock level |

### Sub-skill type labels

| Key | Default value |
|-----|--------------|
| `JSON.Type.Passive` | `&a&lPassive&r` |
| `JSON.Type.Active` | `&4&lActive&r` |
| `JSON.Type.SuperAbility` | `&d&lSuper Ability&r` |

### Hover display keys

| Key | Default value | Purpose |
|-----|--------------|---------|
| `JSON.Hover.Rank` | `&e&lRank:&r &f{0}` | Current rank display (`{0}` = rank number) |
| `JSON.Hover.NextRank` | `&7&oNext upgrade at level {0}` | Next rank unlock hint |
| `JSON.Hover.Mystery` | `&7???` | Shown for unknown/locked content |
| `JSON.Hover.SkillName` | `&3{0}&r` | Sub-skill name in hover (`{0}` = name) |
| `JSON.Hover.MaxRankSkillName` | `&6{0}&r` | Sub-skill name when at max rank |
| `JSON.Hover.Tips` | `Tips` | Tips section header |
| `JSON.Hover.AtSymbolSkills` | `&e@` | The `@` symbol shown next to skill level |

### Rank unlock notification

```properties
JSON.SkillUnlockMessage=&6[ mcMMO&e @&3{0} &6Rank &3{1}&6 Unlocked! ]
```

`{0}` = level reached, `{1}` = rank number unlocked.

### Lucky perks

| Key | Default value |
|-----|--------------|
| `JSON.JWrapper.Perks.Header` | `&6Lucky Perks` |
| `JSON.JWrapper.Perks.Lucky` | `{0}% Better Odds` |

### Skill name labels

Skill names shown in chat and tooltips are controlled by `<Skill>.SkillName` keys, not `JSON.*` keys:

```properties
Mining.SkillName=Mining
Woodcutting.SkillName=Woodcutting
Herbalism.SkillName=Herbalism
# ... one per skill
```

Override these in `locale_override.properties` to rename a skill for your server.

### Sub-skill tip text

Individual sub-skill tooltips display a tips line in the hover panel. Keys follow this pattern:

```
JSON.<Skill>.SubSkill.<SubSkill>.Details.Tips
```

Example:

```properties
JSON.Acrobatics.SubSkill.Roll.Details.Tips=If you hold sneak while falling you can prevent up to twice the damage that you would normally take!
```

Find the key for a specific sub-skill by searching `JSON.<Skill>.SubSkill.<Name>.Details.Tips` in the [en_US locale file](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/locale/locale_en_US.properties).
