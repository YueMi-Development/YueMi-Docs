---
sidebar_position: 1
title: Introduction
---

# Introduction

MMO Mobs is a modern Minecraft server plugin built for PaperMC that lets you create custom mobs using JSON5 configurations. Mobs can spawn with custom stats, bound skills, and custom equipment resolved from the server's item providers.

## Features

- **JSON5 Configurations**: Clean, commentable configuration files under `plugins/MMO-Mobs/mobs/`.
- **Dynamic Stats**: Custom base health and movement speed attributes.
- **Skill Triggers**: Cast skills on triggers like `onAttack` (when the mob attacks) and `onDamaged` (when the mob takes damage).
- **Equipment Integration**: Equip mobs with weapons and armor retrieved from YueMiLibs (such as vanilla keys `minecraft:iron_chestplate` or custom item keys `mmoitems:fire_sword`).
- **Built-in Loop Prevention**: Self-inflicted skill damage is tracked to prevent infinite skill casting loops.
