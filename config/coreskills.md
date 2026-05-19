---
title: coreskills.yml
description: Enable or disable individual mcMMO skills and sub-skills.
published: true
date: 2026-05-17T00:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# coreskills.yml

`coreskills.yml` lets you enable or disable individual mcMMO skills and sub-skills. Default values can be viewed [on GitHub](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/coreskills.yml).

> Changes require a full server restart.
{.is-warning}

---

## How It Works

The file uses a simple pattern. Every entry defaults to `true` (enabled) — you only need to add entries for things you want to change.

**Disable an entire skill** (all sub-skills):
```yaml
Mining:
    Enabled: false
```

**Disable a specific sub-skill** (leave the rest of the skill intact):
```yaml
Acrobatics:
    Roll:
        Enabled: false
```

The sub-skill name used in the config matches the internal key name. The default file only ships with the Acrobatics example, but the same pattern applies to every skill and sub-skill.

---

## Sub-Skill Config Key Names

The key names are derived from the sub-skill's internal name. If you are unsure of the exact key, check the source or experiment — an unrecognised key is simply ignored (defaults to enabled).

### Examples

```yaml
# Disable double drops from Excavation
Excavation:
    Archaeology:
        Enabled: false

# Disable Shake for Fishing without disabling Treasure Hunter
Fishing:
    Shake:
        Enabled: false

# Fully disable Unarmed
Unarmed:
    Enabled: false
```

---

## Notes

- Disabling a **skill** (`Enabled: false` at the skill level) prevents all XP gain and sub-skill procs for that skill.
- Disabling a **sub-skill** still allows XP gain in the parent skill; it just stops the specific proc from triggering.
- Permissions can also be used to restrict skills and sub-skills per player or group — see [Permissions](/permissions).
