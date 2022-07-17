---
title: Permissions
description: Permission nodes used within mcMMO
published: true
date: 2022-07-17T21:46:08.005Z
tags: permissions
editor: markdown
dateCreated: 2022-07-17T21:10:51.772Z
---

# Permissions

Before reading further, it should be known that mcMMO permission nodes are set to default values which automatically ensure every player can use mcMMO properly and gives server operators access to admin tools within mcMMO, you can customize mcMMO permission nodes if you want but it should not be necessary unless you have your permission plugin set to deny all nodes by default for users on your server.

## Complete List of Permissions

The authoritative source for permissions is [plugin.yml](https://github.com/mcMMO-Dev/mcMMO/blob/master/src/main/resources/plugin.yml#L185) which is part of mcMMO source code, it is bundled inside mcMMO.jar when mcMMO is compiled and contains every permission for mcMMO.

## Recommended Permissions

The recommended permission to give players is ***mcmmo.defaults*** this gives players access to everything outside of admin tools

# Perk Permissions

Contained within mcMMO are perk permissions, which give players bonuses so long as the permission is active on the player.