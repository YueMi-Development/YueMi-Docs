---
sidebar_position: 2
title: GuiBuilder
---

# GuiBuilder

> Part of **YueMi-MC-Libs** · GUI Module

Layer-based GUI builder for creating multi-layered interactive inventories.

## GuiApi

Entry point for creating GUI builders and items.

```java
public interface GuiApi {
    @NotNull GuiBuilder createBuilder();
    @NotNull GuiItem.Builder createItemBuilder();
    @NotNull AnvilInputBuilder createAnvilInputBuilder();
    @NotNull SignInputBuilder createSignInputBuilder();
}
```

## GuiBuilder

```java
public interface GuiBuilder {
    @NotNull GuiBuilder title(@NotNull String title);
    @NotNull GuiBuilder rows(int rows);                           // 1-6 rows
    @NotNull GuiBuilder addLayer(@NotNull GuiLayer layer);
    @NotNull GuiBuilder createLayer(@NotNull String id, int priority,
                                    @NotNull Consumer<GuiLayerBuilder> configurator);
    @NotNull GuiBuilder closePolicy(@NotNull ClosePolicy policy);
    @NotNull GuiBuilder onClose(@NotNull Consumer<Player> callback);
    @NotNull Gui build();
}
```

## GuiLayer

Each layer has an ID, priority (higher = rendered on top), and a configurator.

```java
// In a layer configurator:
void configure(GuiLayerBuilder layer) {
    layer.fill(Material.BLACK_STAINED_GLASS_PANE);  // fill entire layer
    layer.set(slot, guiItem);                       // set item at slot
    layer.remove(slot);                             // clear slot
}
```

## ClosePolicy

```java
public enum ClosePolicy {
    CLOSE,    // Close normally, invoke callbacks
    REOPEN,   // Prevent closing, auto-reopen next tick
    NOTHING   // Close without invoking any callbacks
}
```
