---
title: IsEquippedAsAccessory Condition
sidebar_position: 3
---

# IsEquippedAsAccessory Condition

`isequippedasaccessory` returns `true` when the source item that triggered the skill is currently equipped in an accessory slot (any BELT / GLOVES / RING / NECKLACE slot defined by MC-MMO-Accessories).

The condition is a soft integration — it requires MC-MMO-Accessories at runtime. If the plugin isn't installed (or the API isn't registered), the condition falls back to `false`.

## Details

When a skill is fired by an equipped accessory, MMO Mechanics receives the source item via the `source_item` skill-context variable. `isequippedasaccessory` looks up that item against `AccessoriesApi.getAllEquipped(caster)` and returns `true` if the item is currently in any accessory slot.

If no `source_item` is set, the condition falls back to checking whether the caster has **any** accessory equipped. This makes the condition useful in skills that just need the player to be "wearing accessories" without binding to a specific item.

## Example Configuration

```json5
{
  name: "Ring Power Strike",
  mechanics: [
    {
      mechanic: "damage{amount=15}",
      targeter: "target",
      conditions: ["isequippedasaccessory"]
    }
  ]
}
```

## Cross-plugin Requirements

- **MC-MMO-Accessories** must be installed and its API registered (it does so automatically in `onEnable`). The condition uses reflection on the public `AccessoriesApi` interface to look up equipped items, so a missing plugin or missing API registration both fall back to `false` without throwing.
- The `source_item` skill-context variable is set by MMO Mechanics' own `fireTrigger` / `castSkill` paths and by MC-MMO-Accessories' in-slot listener when an equipped accessory dispatches a skill.
