---
sidebar_position: 1
title: Introduction
---

# Introduction

MMO Items is a modern Minecraft server plugin built for PaperMC that allows you to define custom items (weapons, armor, consumables) using JSON5 configuration files. It supports binding custom skills (from MMO Mechanics) to specific triggers (like attacking or interacting).

## Features

- **JSON5 Configuration**: Define items with comments, single quotes, and trailing commas support.
- **Persistent Identification**: Custom items are tagged using Bukkit's `PersistentDataContainer` (PDC) under the key `mmoitems:id`.
- **YueMi-MC-Libs Integration**: Natively registers as a library `ItemProvider`, letting other plugins and menus resolve custom items using `mmoitems:itemId` keys.
- **Skill Binding**: Bind skills to items on `onAttack` (melee attacks) or `onInteract` (right-clicking).
