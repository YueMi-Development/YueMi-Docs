---
sidebar_position: 2
title: ItemsApi
---

# ItemsApi

> Part of **YueMi-MC-Libs** · Items Module

Main entry point for the items system.

## ItemsApi

```java
public interface ItemsApi {
    void registerProvider(@NotNull String namespace, @NotNull ItemProvider provider);
    @Nullable ItemStack getItem(@NotNull String key, int amount);
    boolean giveItem(@NotNull Player player, @NotNull String key, int amount);
    boolean takeItem(@NotNull Player player, @NotNull String key, int amount);
    int getItemCount(@NotNull Player player, @NotNull String key);
}
```

**Key format:** `namespace:id` (e.g. `itemsadder:diamond_hoe`)

The namespace determines which registered provider handles the key.

## ItemProvider

Implement this interface to add support for a custom item backend.

```java
public interface ItemProvider {
    @NotNull String getName();
    boolean isAvailable();
    @Nullable ItemStack getItem(@NotNull String id, int amount);
    boolean giveItem(@NotNull Player player, @NotNull String id, int amount);
    boolean takeItem(@NotNull Player player, @NotNull String id, int amount);
    int getItemCount(@NotNull Player player, @NotNull String id);
}
```

## Registering a Custom Provider

```java
public class MyItemProvider implements ItemProvider {
    @Override
    public @NotNull String getName() { return "myitems"; }

    @Override
    public boolean isAvailable() { return true; }

    @Override
    public @Nullable ItemStack getItem(@NotNull String id, int amount) {
        if (!id.startsWith("myitems:")) return null;
        String itemId = id.substring("myitems:".length());
        return myDatabase.getItem(itemId, amount);
    }

    @Override
    public boolean giveItem(@NotNull Player player, @NotNull String id, int amount) {
        ItemStack item = getItem(id, amount);
        if (item == null) return false;
        return player.getInventory().addItem(item).isEmpty();
    }

    @Override
    public boolean takeItem(@NotNull Player player, @NotNull String id, int amount) {
        // implementation
    }

    @Override
    public int getItemCount(@NotNull Player player, @NotNull String id) {
        // implementation
    }
}

// Register:
items.registerProvider("myitems", new MyItemProvider());

// Use:
items.giveItem(player, "myitems:special_sword", 1);
```
