---
sidebar_position: 1
title: GUI Module
---

# GUI Module

> Part of **YueMi-MC-Libs**

Layer-based GUI builder with support for dynamic items, anvil input, and sign editing.

## APIs

| API | Description |
|-----|-------------|
| [GuiBuilder](./GuiBuilder) | Layer-based GUI builder |
| [GuiItem](./GuiItem) | Dynamic GUI items with conditions and click handlers |
| [InputBuilders](./InputBuilders) | Anvil and sign text input |

## Quick Start

```java
GuiApi gui = api.getGui();

Gui gui = gui.createBuilder()
    .title("My GUI")
    .rows(6)
    .createLayer("main", 0, layer -> {
        layer.fill(Material.GRAY_STAINED_GLASS_PANE);
        layer.set(22, gui.createItemBuilder()
            .item(Material.DIAMOND)
            .onClick(ctx -> ctx.getPlayer().sendMessage("Clicked diamond!"))
            .build());
    })
    .build();

gui.open(player);
```
