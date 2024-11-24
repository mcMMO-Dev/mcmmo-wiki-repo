---
title: mcMMO API
description: mcMMO API
published: true
date: 2024-11-24T02:14:07.767Z
tags: api
editor: markdown
dateCreated: 2024-11-24T02:14:07.767Z
---

# API
> This page is intended for minecraft modders / Java developers.
{.is-warning}

> This page is under construction, **you** can add to it and help complete it!
{.is-warning}

# Some advice...
mcMMO is a legacy code base, if you are having difficulty understanding it's archaic ways, feel free to ask me questions on the mcMMO discord and I will answer when I'm able to!

# Adding mcMMO to your project

## Using Maven
Add to your pom.xml...
```xml
<repository>
  <id>mcmmo-repo</id>
  <url>https://nexus.neetgames.com/repository/maven-public</url>
</repository>
```

```xml
<dependency>
  <groupId>com.gmail.nossr50.mcMMO</groupId>
  <artifactId>mcMMO</artifactId>
  <version>LATEST</version>
  <scope>provided</scope>
</dependency>
```
## Using Gradle
Coming soon...

# Useful Packages
`com.gmail.nossr50.api` Contains some public static helper methods
`com.gmail.nossr50.events` Home of a lot of mcMMO events
`com.gmail.nossr50.mcMMO` the main class of the plugin, contains some useful public static APIs
`com.gmail.nossr50.util.player.UserManager` contains public static methods for getting mcMMO relevant state for players

# Examples
Coming one day.. maybe..