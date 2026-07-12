---
title: mcMMO API
description: mcMMO API
published: true
date: 2026-07-12T00:00:00.000Z
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

Replace `2.3.001-SNAPSHOT` with the version you want to target.

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
  <version>2.3.001-SNAPSHOT</version>
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
    compileOnly 'com.gmail.nossr50.mcMMO:mcMMO:2.3.001-SNAPSHOT'
}
```

Or for Kotlin DSL (`build.gradle.kts`):
```kotlin
repositories {
    maven("https://nexus.neetgames.com/repository/maven-public")
}

dependencies {
    compileOnly("com.gmail.nossr50.mcMMO:mcMMO:2.3.001-SNAPSHOT")
}
```

# Useful Packages
- `com.gmail.nossr50.api`, Contains public static helper methods
- `com.gmail.nossr50.events`, Home of mcMMO events (listen to these to react to mcMMO actions)
- `com.gmail.nossr50.mcMMO`, The main plugin class; contains useful public static APIs
- `com.gmail.nossr50.util.player.UserManager`, Contains public static methods for getting mcMMO state for players

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

// the skill name is case-insensitive; the last argument is the XP gain reason
ExperienceAPI.addXP(player, "Mining", 500, "UNKNOWN");
```

## Listening to mcMMO events

```java
import com.gmail.nossr50.events.experience.McMMOPlayerLevelUpEvent;
import com.gmail.nossr50.datatypes.skills.PrimarySkillType;
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

## Running commands or code on level up

mcMMO can dispatch commands or call back into your plugin when players level up. Registrations return a `UUID` you can use to unregister later; they survive mcMMO config reloads and are removed automatically when your plugin is disabled.

```java
import com.gmail.nossr50.api.LevelUpCommandAPI;
import com.gmail.nossr50.commands.levelup.LevelUpCommand;
import com.gmail.nossr50.datatypes.skills.PrimarySkillType;
import java.util.Set;
import java.util.UUID;

// Dispatch a command when a player reaches Mining 100
UUID commandId = LevelUpCommandAPI.registerCommand(myPlugin, LevelUpCommand.builder()
        .withSkill(PrimarySkillType.MINING)
        .withLevels(Set.of(100))
        .command("say {@player} mastered {@skill}!")
        .build());

// Or run your own code on every level up
UUID handlerId = LevelUpCommandAPI.registerHandler(myPlugin,
        (player, skill, levelsGained, powerLevel) -> {
            // your logic here
        });

LevelUpCommandAPI.unregister(commandId);
```

Server owners can also configure level up commands without a plugin; see [level_up_commands.yml](/config/level-up-commands).
