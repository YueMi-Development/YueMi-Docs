---
title: Developer API
sidebar_position: 99
---

# Developer API Documentation

Magic Auction provides a Java API allowing other plugins to interact with the game.

## Dependency Integration

To consume the Magic Auction API, add the dependency to your project:

### Gradle (Kotlin DSL)
```kotlin
dependencies {
    compileOnly("org.yuemi:MagicAuction-api:<version>")
}
```

### Maven (pom.xml)
```xml
<dependency>
    <groupId>org.yuemi</groupId>
    <artifactId>MagicAuction-api</artifactId>
    <version>VERSION</version>
    <scope>provided</scope>
</dependency>
```

---

## Accessing the API

The API can be accessed via the standard Bukkit Services Manager:

```java
import org.yuemi.magicauction.api.MagicAuctionApi;
import org.bukkit.Bukkit;

MagicAuctionApi api = Bukkit.getServicesManager().load(MagicAuctionApi.class);
if (api != null) {
    // API is available
}
```

---

## API Capabilities

The `MagicAuctionApi` interface provides simple utility features:

```java
package org.yuemi.magicauction.api;

import org.bukkit.entity.Player;
import org.jetbrains.annotations.NotNull;

public interface MagicAuctionApi {

    /**
     * Sends a mini-message formatted message to a player.
     */
    void sendMessage(
            @NotNull Player player,
            @NotNull String message
    );

    /**
     * Checks if a player has features enabled.
     */
    boolean isFeatureEnabled(@NotNull Player player);
}
```
