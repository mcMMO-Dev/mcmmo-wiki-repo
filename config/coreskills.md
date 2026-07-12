---
title: coreskills.yml
description: Legacy skill toggle file; only the Acrobatics Roll toggle still has an effect.
published: true
date: 2026-07-12T00:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# coreskills.yml

`coreskills.yml` ships in the mcMMO config folder, but almost every entry in it is inert. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/coreskills.yml).

> Changes require a full server restart.
{.is-warning}

---

## What Actually Works

The only key that changes anything is `Acrobatics.Enabled`. Setting it to `false` stops the Roll sub-skill from being registered:

```yaml
Acrobatics:
    Enabled: false
```

Every other entry in the file, including the primary-skill `Enabled` toggles for other skills and the per-sub-skill `Enabled` toggles, is not read by the code and has no effect.

To restrict which skills or sub-skills players can use, use permissions instead. See [Permissions](/permissions).
