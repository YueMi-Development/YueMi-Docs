---
title: Compatibility
sidebar_position: 98
---

# Compatible Plugins

MC-MMO-Accessories is a thin slot layer on top of MMO Items and MMO Mechanics. It depends on them for slot validation, skill dispatch, and the public API.

---

## MMO Items

- **MMO Items**
  - *Usage*: Slots validate items through `MmoItemsApi.getItemTypes(item)` against the slot's `accepted-types` list (any-of matching). The skill bindings declared in `items/*.json5` (`skills: [{ skill, trigger }]`) are read via `MmoItemsApi.getItemSkills(item)`.
  - `AccessoryInteractionListener` iterates the equipped accessories on `onAttack` / `onRightClick` and calls `MmoMechanicsApi.castSkill(uuid, skillId)` for each binding with a matching `trigger`.
  - Items in MMO Items that aren't in the slot's `accepted-types` are rejected by the GUI with a "This item cannot be equipped" message.

## MMO Mechanics

- **MMO Mechanics**
  - *Usage*: After every successful `equipAccessory` / `unequipAccessory`, MC-MMO-Accessories calls `MmoMechanicsApi.fireTrigger(uuid, "onEquip" / "onUnequip")`. MMO Mechanics finds skills whose JSON5 `triggers: [...]` list includes the matching id and runs them.
  - The `isequippedasaccessory` condition in MMO Mechanics reads the player's accessories through the public `AccessoriesApi` (reflection-based, soft-depend). If MMO-Accessories isn't installed, the condition always returns `false`.
  - The drag-and-drop GUI listener subscribes through YueMiLibs' `EventApi` — no direct `JavaPlugin#registerEvents` calls.

## Storage Backends

- The optional database backends (SQLite, MySQL, MongoDB) are declared as `compileOnly` in the build so the jar stays small. Add the dependency to your build server only if you use that backend.
