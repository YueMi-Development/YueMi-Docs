---
sidebar_position: 4
title: Input Builders
---

# Input Builders

> Part of **YueMi-MC-Libs** · GUI Module

Anvil and sign text input builders for player interaction.

## AnvilInputBuilder

Opens an anvil GUI for single-field text input.

```java
public interface AnvilInputBuilder {
    @NotNull AnvilInputBuilder title(@NotNull String title);           // anvil window title
    @NotNull AnvilInputBuilder text(@NotNull String initialText);     // pre-filled text
    @NotNull AnvilInputBuilder onComplete(@NotNull Consumer<String> callback);
    @NotNull AnvilInputBuilder onCancel(@NotNull Runnable callback);
    void open(@NotNull Player player);
}
```

**Example:**

```java
gui.createAnvilInputBuilder()
    .title("Enter your nickname")
    .text(player.getName())
    .onComplete(name -> player.sendMessage("Nickname set to: " + name))
    .onCancel(() -> player.sendMessage("Cancelled"))
    .open(player);
```

## SignInputBuilder

Opens a sign editor for multi-line text input.

```java
public interface SignInputBuilder {
    @NotNull SignInputBuilder lines(@NotNull String... lines);           // pre-fill lines
    @NotNull SignInputBuilder onComplete(@NotNull Consumer<String[]> callback);
    void open(@NotNull Player player);
}
```

**Example:**

```java
gui.createSignInputBuilder()
    .lines("Line 1", "", "Your message here", "")
    .onComplete(lines -> {
        player.sendMessage("Sign written: " + String.join("|", lines));
    })
    .open(player);
```
