---
title: Developer API
sidebar_position: 99
--- 

# Developer API Documentation

Bingo Gacha provides a simple API to integrate with other plugins, manage player progress, and listen to custom gameplay events.

## Dependency Integration

To consume the Bingo Gacha API, first ensure you have registered the [YueMi Maven Repository](../../YueMi-API/maven.md) in your project configuration, then add the API dependency:

### Gradle (Kotlin DSL)
```kotlin
dependencies {
    compileOnly("org.yuemi:BingoGacha-api:<version>")
}
```

### Maven (pom.xml)
```xml
<dependency>
    <groupId>org.yuemi</groupId>
    <artifactId>BingoGacha-api</artifactId>
    <version>VERSION</version>
    <scope>provided</scope>
</dependency>
```

---

## Accessing the API

The API can be accessed via `BingoGachaApiProvider` or standard Bukkit Service Manager.

```java
import org.yuemi.bingogacha.api.BingoGachaApi;
import org.yuemi.bingogacha.api.BingoGachaApiProvider;

// Option 1: Using the provider helper
BingoGachaApi api = BingoGachaApiProvider.getApi();

// Option 2: Using Bukkit Services Manager
BingoGachaApi api = Bukkit.getServicesManager().load(BingoGachaApi.class);
```

---

## API Capabilities

The `BingoGachaApi` interface exposes repositories, managers, and template properties:

```java
public interface BingoGachaApi {

    /**
     * @return the active reward manager
     */
    @NotNull
    RewardManager getRewardManager();

    /**
     * @return the active player card repository
     */
    @NotNull
    PlayerCardRepositoryInterface getPlayerCardRepository();

    /**
     * Retrieves a card template by its ID.
     *
     * @param id the template ID
     * @return the template, or null if not found
     */
    @Nullable
    CardTemplate getTemplate(@NotNull String id);

    /**
     * @return a collection of all loaded card templates
     */
    @NotNull
    Collection<CardTemplate> getTemplates();
}
```

---

## Custom Events

You can listen to events fired by Bingo Gacha in your standard Bukkit event listeners.

### `PlayerCardCompleteEvent`
Triggered asynchronously when a player successfully completes a bingo card.

```java
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;
import org.yuemi.bingogacha.api.event.PlayerCardCompleteEvent;

public class MyBingoListener implements Listener {

    @EventHandler
    public void onCardComplete(PlayerCardCompleteEvent event) {
        Player player = event.getPlayer();
        String templateId = event.getCardTemplate().getId();
        
        player.sendMessage("Congratulations on completing " + templateId + "!");
    }
}
```
