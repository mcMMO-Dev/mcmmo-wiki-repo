---
title: Acrobatics
description: View information about the Acrobatics skill for mcMMO!
published: true
date: 2022-08-08T16:22:50.747Z
tags: acrobatics, skills
editor: markdown
dateCreated: 2022-07-16T20:35:16.605Z
---

# Acrobatics

**Acrobatics** is a [skill](/skills) focused around moving gracefully, reducing fall damage and avoiding attacks.

## Experience Gain

Experience in Acrobatics is gained by taking fall damage, successfully rolling on the ground, or successfully dodging attacks.

120XP per half heart of damage is gained when taking fall damage. Assuming no damage is being reduced, it can also be calculated as `(b - 3) * 120` where `b` is the amount of blocks fallen before taking damage. Any reduction of damage by use of hay bales, potions, enchantments etc. will reduce the amount of experience gained. If a roll or graceful roll as been executed, you will gain 80XP per half heart of damage instead of 120XP. This calculation uses the damage that would have been taken if you had not rolled.

Feather falling will double the amount of XP you earn from falling, regardless of its enchantment level. Keep in mind that feather falling will also reduce the amount of base damage dealt when you fall.

Dodging an attack will give 120XP per half heart of damage dodged. So if you dodged an attack that would have dealt you 3 damage, it would give you 360XP.

### Anti Exploit

There is a config option found in [experience.yml](/config/experience) to prevent users from using AFK acrobatic farms that allow them to farm XP while AFK.

```yml
ExploitFix:
    Acrobatics: true
```

A user will not gain experience if any of the following are true:

- User is holding an enderpearl in their main hand while inside a vehicle.
- User has teleported in the last 5 seconds
- User has landed in the same spot at least once within the last 50 times they have fallen from a high place and gained mcMMO Acrobatics Experience

Additionally, after gaining experience from a fall, there will be a cooldown of 3 seconds before you may gain experience again. If you take more fall damage during this period, extra time is added to the cooldown, starting at an additional 10 seconds and increasing by 1 each time more fall damage is taken before the cooldown is over.

## Active Sub-Skill

### Roll

Rolling is an active sub-skill with a passive component. It provides a chance to negate fall damage based on the player's **Acrobatics** skill level. At level 50, the player has a 50% chance to negate damage, or 100% if **Graceful Roll** is activated. The chance for success is scaled against the Acrobatics skill level in a linear curve. Every level increases the chance to roll successfully by 1%. Therefore, it will always trigger at level 100.

A normal roll can be transformed into a **Graceful Roll** by sneaking while falling. Doing so will double the odds to roll and the amount of damage prevented.

#### Odds

Level | Retro Mode | Roll | Damage Absorbed | Graceful Roll | Damage Absorbed Graceful
|:----:|:-----:|:-----:|:---:|:--:|:--:|
25 | 250 | 25% | 7 | 50% | 14 |
50 | 500 | 50% | 7 | 100% | 14 |
75 | 750 | 75% | 7 | 100% | 14 |
| 100 | 1000 | 100% | 7 | 100% | 14 |

## Passive Sub-Skill

### Dodge

> Dodge unlocks at Level 2 or Level 20 for Retro Mode
{.is-info}

Dodge will give you a chance of reducing incoming damage by half. For instance, if you are receiving 6 damage, you will only receive 3 damage when successfully dodging. You will never dodge an attack if the incoming damage would be lethal, this check is done before dodge reduces incoming damage. Dodge also has a cooldown before it will award XP if the player recently respawned from a death.

Dodge reduces the players damage from various harmful sources. There is a config option in [config.yml](/config/config) to allow Dodge to work for lightning strikes.

```yml
Skills:
    Acrobatics:
        Prevent_Dodge_Lightning: false
        XP_After_Teleport_Cooldown: 5
```
