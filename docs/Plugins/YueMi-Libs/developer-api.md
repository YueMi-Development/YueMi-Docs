---
sidebar_position: 3
title: Developer API
---

# Developer API

YueMi Libs offers a simple and unified API for managing players' economy balances and handling custom or vanilla items across multiple plugins.

---

## Dependency Integration

To use YueMi Libs in your plugin, add the `core-api` dependency to your project.

### Gradle (Kotlin DSL)
```kotlin
repositories {
    maven("https://repo.yuemi.org/releases") // Replace with the actual YueMi Maven Repo URL if different
}

dependencies {
    compileOnly("org.yuemi:core-api:<version>")
}
```

### Maven (pom.xml)
```xml
<repositories>
    <repository>
        <id>yuemi-repo</id>
        <url>https://repo.yuemi.org/releases</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>org.yuemi</groupId>
        <artifactId>core-api</artifactId>
        <version>VERSION</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```

---

## Accessing the API

The entry point to the API is `YueMiLibsProvider`. Ensure your plugin lists `YueMiLibs` in its `softdepend` or `depend` in `plugin.yml`.

```java
import org.yuemi.libs.api.YueMiLibsApi;
import org.yuemi.libs.api.YueMiLibsProvider;

YueMiLibsApi api = YueMiLibsProvider.getApi();
```

---

## Economy API

The Economy API provides standard methods to interact with the active economy provider without coupling your code to Vault or other plugins directly.

### Interacting with Economy
```java
import org.yuemi.libs.api.economy.EconomyApi;

EconomyApi economy = api.getEconomy();

if (economy.isAvailable()) {
    double balance = economy.getBalance(player);
    
    // Deposit money
    economy.deposit(player, 100.0);
    
    // Withdraw money
    if (economy.withdraw(player, 50.0)) {
        player.sendMessage("Spent $50.00!");
    }
}
```

---

## Item Provider API

The Items API allows you to lookup, give, count, and take items from multiple provider backends using namespace prefixes (`namespace:id`). If no namespace is specified, it defaults to `minecraft`.

### 1. Vanilla Items (`minecraft:`)
Supports material names and bracket-syntax for Custom Model Data.
*   `minecraft:stone`
*   `minecraft:diamond_sword{CustomModelData:102}`

### 2. CraftEngine Custom Items (`craftengine:`)
Integrates directly with CraftEngine's item definitions.
*   `craftengine:fire_sword`
*   `craftengine:mythic:elven_bow`

### Usage Example

```java
import org.yuemi.libs.api.items.ItemsApi;
import org.bukkit.inventory.ItemStack;

ItemsApi items = api.getItems();

// 1. Get an ItemStack
ItemStack sword = items.getItem("minecraft:diamond_sword{CustomModelData:101}", 1);
ItemStack customStaff = items.getItem("craftengine:magic_staff", 1);

// 2. Give an item to a player (drops on ground if inventory is full)
boolean gaveItem = items.giveItem(player, "craftengine:elven_shield", 1);

// 3. Count matching items in player's inventory
int count = items.getItemCount(player, "minecraft:emerald");

// 4. Take items from player inventory
boolean tookItems = items.takeItem(player, "minecraft:emerald", 5);
if (tookItems) {
    player.sendMessage("Successfully spent 5 Emeralds!");
}
```
