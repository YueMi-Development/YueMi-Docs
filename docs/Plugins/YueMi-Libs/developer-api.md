---
sidebar_position: 99
title: Developer API
---

# Developer API

YueMi Libs offers a simple and unified API for managing players' economy balances, handling custom or vanilla items across multiple plugins, building GUIs, and subscribing to Bukkit events in a typed way.

---

## Dependency Integration

To use YueMi Libs in your plugin, add the relevant `core-api` and per-feature module dependencies.

### Gradle (Kotlin DSL)

```kotlin
repositories {
    maven("https://repo.yuemi.my.id/repository/maven-public/")
}

dependencies {
    implementation("org.yuemi:YueMiLibs-api:2.3.12")
}
```

### Maven (pom.xml)
```xml
<repositories>
    <repository>
        <id>yuemi-repo</id>
        <url>https://repo.yuemi.my.id/repository/maven-public/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>org.yuemi</groupId>
        <artifactId>YueMiLibs-api</artifactId>
        <version>2.3.12</version>
        <scope>compile</scope>
    </dependency>
</dependencies>
```

---

## Accessing the API

The entry point is `YueMiLibsProvider`. List `YueMiLibs` in `softdepend` or `depend` of your `plugin.yml`.

```java
import org.yuemi.libs.api.YueMiLibsApi;
import org.yuemi.libs.api.YueMiLibsProvider;

YueMiLibsApi api = YueMiLibsProvider.getApi();
```

---

## Event Subscription (`EventApi`)

YueMi Libs wraps Bukkit's `Listener` registration in a typed, centralised API. Plugins don't have to call `getPluginManager().registerEvents(...)` directly.

```java
import org.yuemi.libs.api.event.EventApi;
import org.yuemi.libs.api.event.EventApiProvider;
import org.bukkit.event.EventPriority;
import org.bukkit.event.entity.EntityDamageByEntityEvent;

EventApi events = EventApiProvider.getApi();
events.bukkit().subscribe(EntityDamageByEntityEvent.class)
        .priority(EventPriority.MONITOR)
        .ignoreCancelled(true)
        .handler(event -> {
            if (event.getDamager() instanceof org.bukkit.entity.Player p) {
                p.sendActionBar("You hit something!");
            }
        });
```

The same shape works for any Bukkit event. Custom events can be added under a namespace via `EventApi.registerProvider(name, provider)`.

`PlayerEvents` / `EntityEvents` / `BlockEvents` are typed shortcuts over the same `bukkit().subscribe(...)` surface.

---

## GUI Building (`GuiApi`)

`GuiApi` lets a plugin build a multi-layer chest GUI without writing the listener:

```java
import org.yuemi.libs.api.gui.GuiApi;
import org.yuemi.libs.api.gui.GuiProvider;
import org.yuemi.libs.api.gui.SlotBehavior;
import org.yuemi.libs.api.gui.GuiItem;

GuiApi gui = GuiProvider.getApi();

var myGui = gui.createBuilder()
        .title("<gold>My Menu</gold>")
        .rows(3)
        .createLayer("background", 0, layer -> layer.fill(GuiItem.builder()
                .item(p -> new org.bukkit.inventory.ItemStack(org.bukkit.Material.BLACK_STAINED_GLASS_PANE))
                .behavior(SlotBehavior.NONE)            // display-only, can't be picked up
                .build()))
        .createLayer("actions", 1, layer -> layer.setItem(13, GuiItem.builder()
                .item(p -> /* icon */)
                .behavior(SlotBehavior.input())           // accepts drops from inventory
                .onClick((p, ctx) -> p.closeInventory())
                .build()))
        .build();

// Make a slot a place-input slot (so a cursor drop into a placeholder is PLACE not SWAP).
myGui.registerInputSlots(java.util.Set.of(13));

myGui.open(player);
```

Per-slot behaviour flags (`allowPickup`, `allowPlace`, `allowShift`, `allowDrag`) live in `SlotBehavior`. `SlotBehavior.NONE` makes a slot display-only; `SlotBehavior.input()` allows place/drag/shift; `SlotBehavior.output()` allows pickup only.

`GuiListener` (internal to YueMi Libs) honours those behaviours and the per-GUI `inputSlots` set, so a consumer doesn't have to roll its own `InventoryClickEvent` handler for slot-based GUIs.
