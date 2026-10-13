---
sidebar_position: 1
title: Introduction
---

# Introduction

MMO Items is a modern Minecraft server plugin built for PaperMC that allows you to define custom items (weapons, armor, consumables, accessories) using JSON5 configuration files. Each item can bind skills from MMO Mechanics to a trigger so that attacking with or interacting while holding the item casts the skill.

## Features

- **JSON5 Configuration** — define items with comments, single quotes, trailing commas, and unquoted field names.
- **Persistent Identification** — every custom item carries a Bukkit `PersistentDataContainer` entry under the `mmoitems:id` key, plus a comma-joined `mmoitems:types` list.
- **YueMi-MC-Libs Integration** — natively registers as a library `ItemProvider` under the `"mmoitems"` namespace, so other plugins and menus can resolve items using the `mmoitems:itemId` syntax.
- **Skill Binding Surface** — items declare `skills: [{ skill, trigger }]` in their JSON5 config. MMO Mechanics owns the trigger names (`onAttack`, `onDamaged`, `onEquip`, `onUnequip`, `onTimer`, `command`, ...). MMO Items exposes the bindings through `MmoItemsApi.getItemSkills(ItemStack)` so other plugins can dispatch without going through the in-hand listener.
- **Multi-Type Items** — items can declare multiple types (e.g. `["BELT", "WAIST", "ARMOR"]`) for any-of matching against slot `accepted-types` in MC-MMO-Accessories.

## Skill Bindings

Each item config has a `skills` array. The `trigger` value is interpreted by MMO Mechanics — see [MMO Mechanics Skill Triggers](../MMO-Mechanics/configs/skill-config) for the full list. Common values are:

- `onAttack` — fired when hitting an entity with the item in main hand.
- `onInteract` — fired when right-clicking while holding the item.
- `onEquip` / `onUnequip` — fired when the item is placed in or removed from an accessory slot (used by MC-MMO-Accessories).
- `onDamaged` — fired when the wearer is hit (used for defensive accessories).

```json5
{
  name: "<red>Fire Sword</red>",
  material: "DIAMOND_SWORD",
  lore: ["<gray>A burning blade forged in nether flames.</gray>"],
  types: ["WEAPON", "SWORD"],
  skills: [
    { skill: "fire_breath", trigger: "onAttack" }
  ]
}
```

The `ItemSkillConfig` record is a public DTO in `org.yuemi.mmoitems.api.item`:

```java
public record ItemSkillConfig(@NotNull String skill, @Nullable String trigger) {}
```

Use `MmoItemsApi.getItemSkills(itemStack)` to read it back.
