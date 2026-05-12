---
title: mcMMO API
description: mcMMO API
published: true
date: 2024-11-24T02:18:42.087Z
tags: api
editor: markdown
dateCreated: 2024-11-24T02:14:07.767Z
---

# API
> This page is intended for Minecraft modders / Java developers.
{.is-info}

# Some advice...
mcMMO is a legacy code base, if you are having difficulty understanding it's archaic ways, feel free to ask me questions on the mcMMO discord and I will answer when I'm able to!

# Adding mcMMO to your project

Replace `2.2.052-SNAPSHOT` with the version you want to target.

## Using Maven
Add to your `pom.xml`:
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
  <version>2.2.052-SNAPSHOT</version>
  <scope>provided</scope>
</dependency>
```

## Using Gradle
Add to your `build.gradle`:
```groovy
repositories {
    maven {
        url 'https://nexus.neetgames.com/repository/maven-public'
    }
}

dependencies {
    compileOnly 'com.gmail.nossr50.mcMMO:mcMMO:2.2.052-SNAPSHOT'
}
```

Or for Kotlin DSL (`build.gradle.kts`):
```kotlin
repositories {
    maven("https://nexus.neetgames.com/repository/maven-public")
}

dependencies {
    compileOnly("com.gmail.nossr50.mcMMO:mcMMO:2.2.052-SNAPSHOT")
}
```

# Useful Packages
- `com.gmail.nossr50.api` — Contains public static helper methods
- `com.gmail.nossr50.events` — Home of mcMMO events (listen to these to react to mcMMO actions)
- `com.gmail.nossr50.mcMMO` — The main plugin class; contains useful public static APIs
- `com.gmail.nossr50.util.player.UserManager` — Contains public static methods for getting mcMMO state for players

# Examples

## Getting a player's skill level

```java
import com.gmail.nossr50.api.ExperienceAPI;
import com.gmail.nossr50.datatypes.skills.PrimarySkillType;

int miningLevel = ExperienceAPI.getLevel(player, PrimarySkillType.MINING);
```

## Getting a player's power level

```java
import com.gmail.nossr50.api.ExperienceAPI;

int powerLevel = ExperienceAPI.getPowerLevel(player);
```

## Adding XP to a skill

```java
import com.gmail.nossr50.api.ExperienceAPI;
import com.gmail.nossr50.datatypes.skills.PrimarySkillType;

ExperienceAPI.addXp(player, PrimarySkillType.MINING, 500);
```

## Listening to mcMMO events

```java
import com.gmail.nossr50.events.skills.McMMOPlayerLevelUpEvent;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;

public class MyListener implements Listener {
    @EventHandler
    public void onLevelUp(McMMOPlayerLevelUpEvent event) {
        // Fired whenever a player levels up a skill
        PrimarySkillType skill = event.getSkill();
        int newLevel = event.getSkillLevel();
    }
}
```
