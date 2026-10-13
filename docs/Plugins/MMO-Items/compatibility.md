---
title: Compatibility
sidebar_position: 98
---

# Compatible Plugins

MMO Items works in tandem with library and gameplay plugins to provide custom item providers and skill bindings.

---

## YueMi-MC-Libs

- **YueMi-MC-Libs** (Direct Integration)
  - *Usage*: MMO Items natively registers a custom `ItemProvider` under the `"mmoitems"` namespace. Other plugins (like custom GUI menus or crafting engines) can query, check, give, or take MMO items using the standard namespace identifier format: `mmoitems:itemId`.

## MMO Mechanics

- **MMO Mechanics** (Direct Integration)
  - *Usage*: Custom items can bind skills from MMO Mechanics via the `skills: [{ skill, trigger }]` JSON5 block. The `trigger` value is interpreted by MMO Mechanics — the standard trigger ids are `onAttack`, `onDamaged`, `onEquip`, `onUnequip`, `onTimer`, and `command`.
  - MMO Items reads those bindings from JSON5 and exposes them through `MmoItemsApi.getItemSkills(ItemStack)` so MMO Mechanics (and other plugins) can dispatch skills without going through the in-hand listener or reflection.

## MMO Accessories

- **MC-MMO-Accessories** (Direct Integration)
  - *Usage*: MC-MMO-Accessories consumes the items API to:
    - match slot `accepted-types` against `MmoItemsApi.getItemTypes(item)` (any-of matching).
    - read the `skills: []` list via `MmoItemsApi.getItemSkills(item)` for in-slot trigger dispatch on `onAttack` / `onRightClick`.
  - Items in MMO Items that are not in the slot's `accepted-types` are rejected by the accessories GUI with a "This item cannot be equipped" message.
