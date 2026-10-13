---
sidebar_position: 1
title: Introduction
---

# Introduction

MMO Mechanics is a modern Minecraft server plugin built for PaperMC that introduces an event-driven skill system. It provides mechanics, conditions, targeters, and custom triggers to configure modular and highly dynamic gameplay mechanics on your server.

## Features

- **Event-driven Skill System:** Register and trigger skills based on standard gameplay events (combat, lifecycle, projectile) **or** on accessory/armor equip/unequip. All listeners run through YueMi-MC-Libs' `EventApi` so consumers don't call `getPluginManager().registerEvents(...)` directly.
- **Rich Targeter Suite:** Match entities and locations using single/multi entity targeters, rings, cones, spheres, block arrays, and escaped paths.
- **Dynamic Conditions:** Gate skill execution with conditions such as time-of-day checks, or `isequippedasaccessory` to require the caster to be wearing the source item.
- **Modular Mechanics:** Execute actions like delays, custom lightning storms, and particle fields.
- **Public Trigger API:** `MmoMechanicsApi.fireTrigger(UUID caster, String triggerId)` lets other plugins dispatch trigger-based skill execution through `TriggerManager`. `castSkill(UUID, String skillId)` is still available for direct manual casts (e.g. `/mmomechanics cast`).
- **Equip / Unequip Triggers:** `EquipTriggerRegistration` listens to Paper's `PlayerArmorChangeEvent` (with a Spigot fallback) and fires `onEquip` / `onUnequip` whenever an armor slot transitions. The same trigger ids are also used by MC-MMO-Accessories for accessory slots.
