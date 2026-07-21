---
title: Item Configurations
sidebar_position: 2
---

# Item Configuration

Item templates are configured under the `items/` directory as individual YAML (`.yml`) files. They define the physical size, value, display properties, and rewards of the mystery items.

---

## Example Item Configs

### 1. Virtual Item
```yaml
id: "golden_ticket"
rarity: "common"
type: "consumable"
base-item: "minecraft:paper"
display-name: "Golden Ticket"
desc: "Allows entering exclusive auctions!"
width: 3
height: 1
custom-model-data: 1001
worth: 50.0
virtual-item: true
```

### 2. Container (Physical / Reward-based) Item
```yaml
id: "mysterious_box"
rarity: "super_rare"
type: "collectible"
base-item: "minecraft:chest"
display-name: "Mysterious Box"
desc: "A mysterious container containing unknown treasure!"
width: 2
height: 2
custom-model-data: 0
worth: 300.0
virtual-item: false
rewards:
  - type: "item"
    id: "golden_ticket"
    amount: 2
  - type: "item"
    id: "lucky_charm"
    amount: 1
  - type: "item"
    id: "diamond_block"
    amount: 2
```

---

## Configuration Properties

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `id` | String | *Required* | Unique item ID matching the filename. |
| `rarity` | String | *Required* | Rarity ID referencing a file in `rarities/`. |
| `type` | String | *Required* | Item type ID referencing a file in `types/`. |
| `base-item` | String | *Required* | The raw Minecraft material key (e.g. `minecraft:chest`). Resolved via YueMiLibs. |
| `display-name` | String | — | Custom display name of the item stack (supports Adventure MiniMessage formatting). |
| `desc` | String | — | Description lore text (formatted in white). |
| `width` | Integer | 1 | Item width in slots for chest container packing (1 to 6). |
| `height` | Integer | 1 | Item height in slots for chest container packing (1 to 3). |
| `custom-model-data` | Integer | 0 | Resource pack CustomModelData value. |
| `worth` | Double | 0.0 | Financial value of the item in the auction system. |
| `virtual-item` | Boolean | false | If `true`, the winner receives the item's `worth` in currency. If `false`, the rewards list is evaluated and distributed. |
| `rewards` | List | — | List of rewards distributed when a non-virtual item is won. Supports type `"item"` referencing other custom items. |
