---
title: Compatibility
sidebar_position: 98
---

# Compatible Plugins

MMO Items works in tandem with library and gameplay plugins to provide custom item providers and skills triggers.

---

## YueMi-MC-Libs

* **YueMi-MC-Libs** (Direct Integration)
  * *Usage*: MMO Items natively registers a custom `ItemProvider` under the `"mmoitems"` namespace. Other plugins (like custom GUI menus or crafting engines) can query, check, give, or take MMO items using the standard namespace identifier format: `mmoitems:itemId`.

## MMO Mechanics

* **MMO Mechanics** (Direct Integration)
  * *Usage*: Custom items can bind active mechanics skills from MMO Mechanics to triggers like attacks (`onAttack`) and right-clicks (`onInteract`).
