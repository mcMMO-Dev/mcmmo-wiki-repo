---
title: hidden.yml
description: Hidden (internal) mcMMO configuration reference.
published: true
date: 2026-07-11T20:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# hidden.yml

`hidden.yml` contains a small number of low-level options that are read directly from the bundled resource inside the `mcMMO.jar`. Unlike other config files it is **never written to disk**; any copy you create in the plugins folder will be ignored. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/hidden.yml).

> This file is labeled "for advanced users only". Its values must be reset after every mcMMO update because the file is always read from inside the jar.
{.is-warning}

---

## Options

| Key | Default | Description |
|-----|---------|-------------|
| `Options.EnchantmentBuffs` | `true` | When `true`, Super Breaker and Giga Drill Breaker are buffed by granting a temporary high-level efficiency enchantment on the tool. When `false`, a haste potion effect is used instead. Enchantment buffs are generally more compatible with custom tools. |

> `Options.Chunklets` and `Options.ConversionRate` appear in this file but are **never read by the code** and have no effect. Both are dead configuration keys left over from older versions. Do not rely on them.
{.is-danger}
