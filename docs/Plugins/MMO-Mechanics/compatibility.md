---
title: Compatibility
sidebar_position: 98
---

# Compatible Plugins

MMO Mechanics works with other plugins to enrich skill definitions, placeholders, and target names.

---

## Placeholder API

*   **PlaceholderAPI** (Direct Integration)
    *   *Usage*: MMO Mechanics natively parses PlaceholderAPI placeholders within targeter expressions and config options (e.g. username placeholder in `playerbyname{name=%player_name%}`).

---

## MC-MMO-Items

*   **MMO Items** (Direct Integration)
    *   *Usage*: Items declared in `items/*.json5` carry `skills: [{ skill, trigger }]` blocks. MMO Mechanics listens to `EntityDamageByEntityEvent` and `PlayerInteractEvent` (via YueMiLibs `EventApi`) and dispatches matching skills from items in the player's hand. Items can also use the equip / unequip trigger flow — placing an item in an accessory slot fires `onEquip`, and `MmoMechanicsApi.fireTrigger` carries it through.

## MC-MMO-Accessories

*   **MC-MMO-Accessories** (Direct Integration)
    *   *Usage*: When a player equips an item via the accessories GUI, MC-MMO-Accessories calls `MmoMechanicsApi.fireTrigger(uuid, "onEquip"/"onUnequip")` after a successful save. MMO Mechanics finds skills bound to the player whose JSON5 `triggers` include the matching id and runs them. The accessory's per-binding in-slot triggers (`onAttack`, `onRightClick`) are dispatched by MC-MMO-Accessories' own listener using `MmoMechanicsApi.castSkill`.
    *   MMO Mechanics' `isequippedasaccessory` condition reads accessory state through MC-MMO-Accessories' public `AccessoriesApi` (reflection-based, soft-depend).

## Vanilla Armor

*   **Paper / Spigot (Built-in)** — `EquipTriggerRegistration` listens to Paper's `PlayerArmorChangeEvent` (with a Spigot fallback tracking `PlayerInventory.getArmorContents()` across click/drag events) and fires `onEquip` / `onUnequip` for vanilla armor changes.
