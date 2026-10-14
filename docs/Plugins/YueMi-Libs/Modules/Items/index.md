---
sidebar_position: 1
title: Items Module
---

# Items Module

> Part of **YueMi-MC-Libs**

Multi-provider item system supporting vanilla Minecraft, Nexo, ItemsAdder, and CraftEngine.

## APIs

| API | Description |
|-----|-------------|
| [ItemsApi](./ItemsApi) | Main items API with provider management |

## Quick Start

```java
ItemsApi items = api.getItems();

// Give an item (auto-detects provider from key namespace)
items.giveItem(player, "nexo:iron_sword", 1);

// Get an item
ItemStack item = items.getItem("itemsadder:diamond_hoe", 1);

// Count items in inventory
int count = items.getItemCount(player, "minecraft:diamond");
```

## Built-in Providers

| Provider | Namespace | Description |
|----------|-----------|-------------|
| **MinecraftItemProvider** | `minecraft` | Vanilla Minecraft items |
| **NexoItemProvider** | `nexo` | Nexo plugin items |
| **ItemsAdderItemProvider** | `itemsadder` | ItemsAdder custom items |
| **CraftEngineItemProvider** | `craftengine` | CraftEngine custom items |
