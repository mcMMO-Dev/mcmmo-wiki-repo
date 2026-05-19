---
title: child.yml
description: Information about the removed child.yml configuration file.
published: true
date: 2026-05-17T00:00:00.000Z
tags: config
editor: markdown
dateCreated: 2026-05-17T00:00:00.000Z
---

# child.yml

> `child.yml` no longer exists. This page is kept to avoid broken links.
{.is-warning}

`child.yml` was a configuration file that allowed customising which skills were treated as "child skills" (skills whose effective level is derived from a combination of other skill levels). It was removed from mcMMO and the child skill relationships are now hardcoded.

## Current Child Skills

The following skills are child skills and their relationships cannot currently be changed via config:

| Child Skill | Parent Skills |
|-------------|---------------|
| Salvage | Fishing + Repair (average) |
| Smelting | Mining + Repair (average) |

Child skill levels are computed as `floor((Parent1 + Parent2) / 2)`.
