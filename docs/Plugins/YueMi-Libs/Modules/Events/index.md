---
sidebar_position: 1
title: Events Module
---

# Events Module

> Part of **YueMi-MC-Libs**

Event subscription system with a fluent builder API and categorized event helpers.

## APIs

| API | Description |
|-----|-------------|
| [EventApi](./EventApi) | Main events API |
| [SubscriptionBuilder](./SubscriptionBuilder) | Fluent event subscription builder |
| [BukkitEvents](./BukkitEvents) | Categorized Bukkit event helpers |

## Quick Start

```java
EventApi events = api.getEvents();

// Subscribe to any event
events.bukkit().subscribe(PlayerJoinEvent.class)
    .filter(e -> !e.getPlayer().hasPlayedBefore())
    .handler(e -> e.getPlayer().sendMessage("Welcome!"))
    .subscribe();

// Use categorized helpers
events.bukkit().player().join()
    .handler(e -> broadcast("Player joined!"))
    .subscribe();
```
