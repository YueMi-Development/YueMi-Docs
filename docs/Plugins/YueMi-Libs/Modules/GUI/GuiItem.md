---
sidebar_position: 3
title: GuiItem
---

# GuiItem

> Part of **YueMi-MC-Libs** · GUI Module

Dynamic GUI items with per-player visibility conditions and click handlers.

## GuiItem

```java
public interface GuiItem {
    @NotNull ItemStack getItemStack(@NotNull Player player);
    boolean shouldRender(@NotNull Player player);    // return false to hide item
    void onClick(@NotNull GuiClickContext context);
}
```

## GuiItem.Builder

```java
public interface GuiItem.Builder {
    // Static item
    @NotNull Builder item(@NotNull ItemStack itemStack);
    @NotNull Builder item(@NotNull String key);             // namespace:id
    @NotNull Builder item(@NotNull String key, int amount);

    // Dynamic item provider
    @NotNull Builder item(@NotNull Function<Player, ItemStack> itemProvider);
    @NotNull Builder itemKey(@NotNull Function<Player, String> keyProvider);
    @NotNull Builder itemKey(@NotNull Function<Player, String> keyProvider, int amount);

    // Visibility condition
    @NotNull Builder condition(@NotNull Predicate<Player> condition);

    // Click handler
    @NotNull Builder onClick(@NotNull BiConsumer<Player, GuiClickContext> handler);

    @NotNull GuiItem build();
}
```

## GuiClickContext

Available in click handlers.

```java
public interface GuiClickContext {
    @NotNull Player getPlayer();
    @NotNull Gui getGui();
    int getSlot();
    @NotNull ItemStack getCurrentItem();
    @NotNull ItemStack getCursorItem();
    void setCursorItem(@NotNull ItemStack item);
    void close();
    boolean isShiftClick();
    ClickType getClickType();
}
```

## Examples

**Static item with click:**

```java
GuiItem item = gui.createItemBuilder()
    .item(Material.DIAMOND_SWORD)
    .onClick((player, ctx) -> player.sendMessage("You clicked the sword!"))
    .build();
```

**Dynamic item based on player:**

```java
GuiItem item = gui.createItemBuilder()
    .itemKey(p -> "minecraft:diamond_sword")
    .condition(p -> p.hasPermission("myplugin.admin"))
    .item(p -> {
        ItemStack sword = new ItemStack(Material.DIAMOND_SWORD);
        ItemMeta meta = sword.getItemMeta();
        meta.setDisplayName("Admin Sword");
        sword.setItemMeta(meta);
        return sword;
    })
    .build();
```
