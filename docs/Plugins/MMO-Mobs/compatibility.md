---
title: Compatibility
sidebar_position: 98
---

# Compatible Plugins

MMO Mobs integrates with the library ecosystem and skills engines to provide modular stats, equipment, and abilities.

---

## YueMi-MC-Libs

* **YueMi-MC-Libs** (Direct Integration)
  * *Usage*: MMO Mobs queries `ItemsApi` from `YueMi-MC-Libs` to resolve and equip armor slots and weapons defined in the mob's config. It supports both vanilla items (`minecraft:iron_chestplate`) and custom items (`mmoitems:fire_sword`).

## MMO Mechanics

* **MMO Mechanics** (Direct Integration)
  * *Usage*: Custom mobs can be bound with skills from MMO Mechanics, allowing them to cast abilities on combat triggers like attacking (`onAttack`) and taking damage (`onDamaged`).
