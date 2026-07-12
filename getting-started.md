---
title: Getting Started
description: "First-time player guide for mcMMO."
published: true
date: 2026-07-12T00:00:00.000Z
tags: getting-started, beginner, mcmmo
editor: markdown
dateCreated: 2025-01-01T00:00:00.000Z
---

# Getting Started with mcMMO

Welcome to mcMMO! This page is a brief, player-focused walkthrough for someone joining a server with mcMMO installed for the first time. It covers what skills are, how XP works, what Super Abilities are, and the small handful of commands you'll use most often.

## What is mcMMO?

mcMMO is a server-side plugin that turns ordinary Minecraft activities into trainable **skills**. Every time you mine stone, chop a tree, swing an axe, or land an arrow, you earn experience in the matching skill. Levels in each skill unlock new abilities -- bonus drops, double damage, automatic crop replanting, fast-felling whole trees, and many more.

Skills are entirely per-player. Nothing in your inventory needs to change to use mcMMO -- the plugin watches what you do and rewards it automatically.

## Your first session

You don't need to do anything special to start. Mine a block, swing your sword, cast a fishing rod, and you'll see XP gains appear in your action bar. A few things worth knowing up front:

- Type `/mcstats` at any time to see every skill, its current level, and progress to the next level.
- Type `/<skillname>` (such as `/mining` or `/archery`) to see the sub-skills you've unlocked and what they do at your current level.
- The skill that levels is the skill that matches the activity. Mining with a pickaxe levels Mining; chopping wood with an axe levels Woodcutting; using the wrong tool gives no XP.
- Skills level much faster when you focus on one or two at a time rather than spreading effort across all of them.
- Some combat and gathering skills have a **Super Ability**. Right-click once with a compatible tool to ready the ability, then use the tool (break an eligible block or land a hit) to trigger it for a short burst of power. Super Abilities have a cooldown.

## How XP works

- Every skill has its own XP pool. Mining XP only goes toward Mining; Archery XP only toward Archery.
- The exact XP per action is configured server-side, but in general: rarer blocks and tougher mobs give more XP than common ones. See each skill's page (e.g. [skills/mining](skills/mining.md)) for the full table.
- Some skills are **child skills** that don't earn XP directly: **Salvage** and **Smelting**. Their level is computed from the average of two parent skills, so you raise them indirectly.

## Essential commands

| Command | What it does |
|---------|--------------|
| `/mcstats` | Show your full skill sheet. |
| `/<skillname>` | Show details for one skill -- e.g. `/mining`, `/archery`, `/herbalism`. |
| `/mctop [skill]` | View the server-wide leaderboard for the given skill (or your overall power level if omitted). |
| `/mcrank` | Show your own rank on every skill leaderboard. |
| `/mcability` | Toggle ability preparation. If disabled, you won't accidentally trigger Super Abilities while building. |
| `/inspect <player>` | Look at another player's skill levels. |
| `/party` | Open the party menu. See [Parties](parties.md). |
| `/mcmmo` | Show plugin info and version. |

A complete command reference is in [Commands](Commands.md).

## Super Abilities at a glance

Most combat and gathering skills have an active **Super Ability**:

| Skill | Super Ability | Triggered with |
|-------|---------------|----------------|
| Mining | Super Breaker (faster ore mining) | Right-click while holding a pickaxe |
| Mining | Blast Mining (TNT efficiency) | Sneak + right-click while holding a pickaxe or the detonator item (default Flint & Steel) to remotely detonate nearby TNT |
| Excavation | Giga Drill Breaker | Right-click while holding a shovel |
| Woodcutting | Tree Feller | Right-click while holding an axe |
| Herbalism | Green Terra | Right-click while holding a hoe |
| Unarmed | Berserk | Right-click with an empty hand |
| Axes | Skull Splitter | Right-click while holding an axe |
| Swords | Serrated Strikes | Right-click while holding a sword |

Each ability has a cooldown (configured server-side, often around 4 minutes). When ready again, you'll see a refresh notification.

## Tips for new players

- **Specialise first, generalise later.** Focus one or two skills to a high level rather than spreading effort thin.
- **Use the right tool for the job.** Mining XP only triggers with a pickaxe; Excavation with a shovel; Woodcutting with an axe; Herbalism with a hoe (or hand). Wrong tool = no XP.
- **Read each skill's page.** The wiki has per-skill pages that list every sub-skill, every config-driven value, and every drop chance.
- **Salvage and Smelting are child skills.** Don't try to grind them directly -- raise Repair, Fishing, and Mining instead.

## Where to go next

- [Skill summary](/skills) -- a one-page overview of every skill.
- Per-skill deep dives: see the **Skills** section in the sidebar.
- [Commands](Commands.md) -- every command and what it does.
- [Permissions](permissions.md) -- for server operators.
- [Parties](parties.md) -- play together and share XP.
- [Configuration](config.md) -- for server operators tuning the plugin.
