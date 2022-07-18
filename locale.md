---
title: Localization
description: Learn how to edit the locale in mcMMO!
published: true
date: 2022-07-18T00:13:13.163Z
tags: locale
editor: markdown
dateCreated: 2022-07-18T00:13:13.163Z
---

# Locale

## Built in translations

mcMMO has several built in translations, you can choose which translation by updating config.yml with the appropriate locale code For a list of built in translations, view this link: https://github.com/mcMMO-Dev/mcMMO/tree/master/src/main/resources/locale

## Info on overriding / customizing locales

Locales are the language files used by mcMMO, they also contain color codes and most of the styling used by mcMMO. You can customize a locale outside of the JAR in version 2.1.51 and up.

Locales can be overridden by placing a file with an appropriate name inside /plugins/mcMMO/locales/

You can find the up to date current en_US locale entries on the [GitHub repo](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/locale/locale_en_US.properties).

Make a new file with the same name as this one, and copy only the strings you want to replace, otherwise you will not see any updated strings as they are changed as your copy of the file will have priority. If you wish to replace every line in some way, feel free to copy the entire contents of this file, just be advised that you will need to be on top of locale updates in mcMMO.

Locales only support ASCII and UTF16 characters at the moment, so you'll need to run special characters through a UTF16 converter (google it) to get them to work. This will be fixed in the future!

The locale name must match the internal file you are overriding (ie: `locale_en_US.properties`) The locale file names are structured like this `locale_XX_XX.properties`, replace XX with your country codes, if you are not overriding `en_US` you will have to change the targetted locale inside `config.yml`.

Locale will first check for a users locale file, if it doesn't exist it will use the files inside the JAR.

If a locale is found, it will use locale entries from that file, and if any entries are missing, it will use entries from en_US inside the JAR

You must restart the server for these changes to take effect. Once you have the locale file set in the config.yml file, you can use the command `/mcmmoreloadlocale` if you make changes to the locale properties file. This command only affects a locale properties file, not a config file.