---
sidebar_position: 4
title: BukkitEvents
---

# BukkitEvents

> Part of **YueMi-MC-Libs** · Events Module

Categorized Bukkit event helpers for player, block, and entity events.

## BukkitEvents

```java
public interface BukkitEvents extends EventProvider {
    @NotNull <T extends Event> SubscriptionBuilder<T> subscribe(@NotNull Class<T> eventClass);
    @NotNull PlayerEvents player();
    @NotNull BlockEvents block();
    @NotNull EntityEvents entity();
}
```

## PlayerEvents

```java
public interface PlayerEvents {
    SubscriptionBuilder<PlayerJoinEvent> join();
    SubscriptionBuilder<PlayerQuitEvent> quit();
    SubscriptionBuilder<PlayerInteractEvent> interact();
    SubscriptionBuilder<PlayerMoveEvent> move();
    SubscriptionBuilder<PlayerChatEvent> chat();
    SubscriptionBuilder<PlayerCommandPreprocessEvent> command();
    SubscriptionBuilder<PlayerRespawnEvent> respawn();
    SubscriptionBuilder<PlayerDeathEvent> death();
    SubscriptionBuilder<PlayerExpChangeEvent> expChange();
    SubscriptionBuilder<PlayerItemBreakEvent> itemBreak();
    SubscriptionBuilder<PlayerInteractEntityEvent> interactEntity();
    SubscriptionBuilder<PlayerBucketEvent> bucket();
    SubscriptionBuilder<PlayerEggThrowEvent> eggThrow();
}
```

## BlockEvents

```java
public interface BlockEvents {
    SubscriptionBuilder<BlockBreakEvent> break_();
    SubscriptionBuilder<BlockPlaceEvent> place();
    SubscriptionBuilder<BlockFromToEvent> spread();
    SubscriptionBuilder<BlockRedstoneEvent> redstone();
    SubscriptionBuilder<LeavesDecayEvent> leavesDecay();
    @NotNull SubscriptionBuilder<BlockPhysicsEvent> physics();
}
```

## EntityEvents

```java
public interface EntityEvents {
    SubscriptionBuilder<EntityDeathEvent> death();
    SubscriptionBuilder<EntityDamageEvent> damage();
    SubscriptionBuilder<EntityExplodeEvent> explode();
    SubscriptionBuilder<EntityTameEvent> tame();
    SubscriptionBuilder<EntityBreedEvent> breed();
    SubscriptionBuilder<CreatureSpawnEvent> spawn();
    SubscriptionBuilder<ProjectileHitEvent> projectileHit();
}
```

## Usage

```java
// Subscribe using categorized helper
events.bukkit().player().join()
    .handler(e -> playerCache.onJoin(e.getPlayer()))
    .subscribe();

// Subscribe using raw event class
events.bukkit().subscribe(PlayerQuitEvent.class)
    .handler(e -> playerCache.onQuit(e.getPlayer()))
    .subscribe();
```
