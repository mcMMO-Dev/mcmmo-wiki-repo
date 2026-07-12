---
title: coreskills.yml
description: Legacy skill toggle file; only the skill-level Acrobatics.Enabled toggle (which gates Roll) still has an effect.
published: true
date: 2026-07-12T00:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# coreskills.yml

`coreskills.yml` ships in the mcMMO config folder with only two entries, and just one of them does anything. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/coreskills.yml).

> Changes require a full server restart.
{.is-warning}

---

## What Actually Works

The only key that changes anything is `Acrobatics.Enabled`. Setting it to `false` stops the Roll sub-skill from being registered:

```yaml
Acrobatics:
    Enabled: false
```

The only other shipped entry, `Acrobatics.Roll.Enabled`, is not read by the code, and the same is true of any other skill or sub-skill `Enabled` entries you add.

To restrict which skills or sub-skills players can use, use permissions instead. See [Permissions](/permissions).
