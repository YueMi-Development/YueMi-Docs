---
sidebar_position: 2
title: EventApi
---

# EventApi

> Part of **YueMi-MC-Libs** · Events Module

Main entry point for the event system.

## EventApi

```java
public interface EventApi {
    @NotNull BukkitEvents bukkit();
    @Nullable EventProvider getProvider(@NotNull String namespace);
    void registerProvider(@NotNull String namespace, @NotNull EventProvider provider);
}
```

## EventProvider

Base interface for event providers. `BukkitEvents` is the built-in implementation.

```java
public interface EventProvider {
    <T extends Event> @NotNull SubscriptionBuilder<T> subscribe(@NotNull Class<T> eventClass);
}
```

## EventSubscription

Returned when a subscription is created. Call `.close()` to unsubscribe.

```java
public interface EventSubscription extends Closeable {
    void close();                              // unsubscribe
    boolean isClosed();                        // check if unsubscribed
}
```
