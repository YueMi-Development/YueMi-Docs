---
sidebar_position: 2
title: Item Definitions
---

# Item Definitions

Custom items are configured in JSON5 files under the `items/` folder. Each file represents a single custom item type where the filename (excluding `.json5`) determines the item's unique registration ID (e.g., `lightning_sword.json5` registers as `mmoitems:lightning_sword`).

## Configuration Structure

The configuration structure supports the following sections:

### 1. Basic Properties
* **`name`** (String): 
  * The display name of the item.
  * Supports MiniMessage formatting (e.g. `<gold>Lightning Sword`).
* **`material`** (String): 
  * The vanilla Minecraft material type (e.g. `DIAMOND_SWORD`, `GOLDEN_APPLE`).
  * Must be a valid Bukkit/Spigot Material name.
* **`custom-model-data`** (Integer, Optional): 
  * Sets the custom model data ID on the item meta. Useful for binding custom resource pack textures.

### 2. Lore
* **`lore`** (List of Strings): 
  * A list of lines shown in the item's tooltip.
  * Supports MiniMessage styling (e.g., `<gray>A blade charged with the power of storms.`).

### 3. Skills
* **`skills`** (List of Objects): 
  * Binds custom skills from MMO Mechanics to this item.
  * Fields:
    * `skill` (String): The skill registration key matching the filename in MMO Mechanics (e.g. `lightning_radius_storm`).
    * `trigger` (String): The event that casts the skill.
      * `onAttack`: Casts the skill when hitting an entity with this item in hand.
      * `onInteract`: Casts the skill when right-clicking while holding this item.

---

## Example Configuration (`lightning_sword.json5`)

```json5
{
  // Custom display name with color coding
  name: "<gold>Lightning Sword",
  
  // Base minecraft item type
  material: "DIAMOND_SWORD",
  
  // Custom model data index
  custom-model-data: 101,
  
  // Hover tooltip lines
  lore: [
    "<gray>A blade charged with the power of storms.",
    "<yellow>Strike enemies to summon lightning!"
  ],
  
  // Bound active triggers
  skills: [
    {
      skill: "lightning_radius_storm",
      trigger: "onAttack"
    }
  ]
}
```
