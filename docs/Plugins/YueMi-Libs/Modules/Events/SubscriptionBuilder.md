---
sidebar_position: 3
title: SubscriptionBuilder
---

# SubscriptionBuilder

> Part of **YueMi-MC-Libs** · Events Module

Fluent builder for creating filtered, handler-attached event subscriptions.

## SubscriptionBuilder

```java
public interface SubscriptionBuilder<T extends Event> {
    @NotNull SubscriptionBuilder<T> filter(@NotNull Predicate<T> predicate);
    @NotNull SubscriptionBuilder<T> handler(@NotNull Consumer<T> handler);
    @NotNull EventSubscription subscribe();
}
```

## Examples

**Basic subscription:**

```java
events.bukkit().subscribe(PlayerJoinEvent.class)
    .handler(e -> e.getPlayer().sendMessage("Welcome!"))
    .subscribe();
```

**Filtered subscription:**

```java
events.bukkit().subscribe(PlayerInteractEvent.class)
    .filter(e -> e.getMaterial() == Material.DIAMOND_SWORD)
    .handler(e -> e.getPlayer().sendMessage("You right-clicked a diamond sword!"))
    .subscribe();
```

**Store subscription to close later:**

```java
EventSubscription sub = events.bukkit().subscribe(PlayerQuitEvent.class)
    .handler(e -> savePlayerData(e.getPlayer()))
    .subscribe();

// Later, when the player leaves:
sub.close();  // unsubscribes
```

**Chained filters:**

```java
events.bukkit().subscribe(EntityDeathEvent.class)
    .filter(e -> e.getEntity() instanceof Player)
    .filter(e -> e.getDroppedExp() > 0)
    .handler(e -> e.setDroppedExp(e.getDroppedExp() * 2))
    .subscribe();
```
