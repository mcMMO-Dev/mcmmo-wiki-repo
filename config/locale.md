---
title: Locale
description: Change the language or messages used by mcMMO
published: true
date: 2024-11-24T01:59:07.533Z
tags: config, language, locale
editor: markdown
dateCreated: 2022-07-17T21:48:13.118Z
---

# Locale

mcMMO supports multiple languages and allows server administrators to customize all in-game messages. Locale files control what text players see for skill notifications, ability messages, chat messages, and more.

## Supported Languages

The following locale files are bundled with mcMMO:

| File | Language |
|------|----------|
| `locale_cs_CZ.properties` | Czech |
| `locale_cy.properties` | Welsh |
| `locale_da.properties` | Danish |
| `locale_de.properties` | German |
| `locale_en_US.properties` | English (US) — default |
| `locale_es.properties` | Spanish |
| `locale_fi.properties` | Finnish |
| `locale_fr.properties` | French |
| `locale_hu_HU.properties` | Hungarian |
| `locale_it.properties` | Italian |
| `locale_ja_JP.properties` | Japanese |
| `locale_ko.properties` | Korean |
| `locale_lt_LT.properties` | Lithuanian |
| `locale_nl.properties` | Dutch |
| `locale_pl.properties` | Polish |
| `locale_pt_BR.properties` | Portuguese (Brazil) |
| `locale_ru.properties` | Russian |
| `locale_sv.properties` | Swedish |
| `locale_th_TH.properties` | Thai |
| `locale_zh_CN.properties` | Chinese (Simplified) |
| `locale_zh_TW.properties` | Chinese (Traditional) |

## Configuring the Locale

To change the language mcMMO uses, set the `Locale` option in `config.yml` to the locale code of your desired language (e.g., `de` for German, `fr` for French, `en_US` for English).

## Customizing Messages

To customize individual messages, copy the desired `locale_*.properties` file from the mcMMO jar into your `plugins/mcMMO/` folder and edit it. mcMMO will use your custom file if it exists in the plugin folder.

## Reloading Locale

You can reload locale files without restarting the server using:

```
/mcmmoreloadlocale
```

This command (alias: `/mcreloadlocale`) reloads all locale files immediately. Requires the `mcmmo.commands.reloadlocale` permission.

## Notes

> Locale files use the Java `.properties` format. Lines starting with `#` are comments. Ensure your file is saved with UTF-8 encoding for proper display of non-ASCII characters.
{.is-info}
