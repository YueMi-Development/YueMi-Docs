---
sidebar_position: 2
title: Mob Definitions
---

# Mob Definitions

Custom mobs are configured in JSON5 files under the `mobs/` directory. The filename (excluding `.json5`) determines the custom mob's registration ID (e.g., `fire_zombie.json5` registers as `fire_zombie`).

## Configuration Structure

The configuration structure supports the following sections:

### 1. Basic Properties
* **`name`** (String): 
  * The custom display name shown above the mob's head.
  * Supports MiniMessage formatting (e.g. `<red>Fire Zombie`).
* **`type`** (String): 
  * The vanilla Minecraft entity type to spawn as the base (e.g., `ZOMBIE`, `SKELETON`, `SPIDER`).
  * Must be a valid Bukkit/Spigot EntityType.

### 2. Stats
* **`health`** (Double, Optional): 
  * Sets the max health attribute and heals the mob to full upon spawning.
* **`speed`** (Double, Optional): 
  * Modifies the base movement speed attribute of the entity.

### 3. Tags
* **`tags`** (List of Strings, Optional): 
  * A list of scoreboard tags written to the entity.

### 4. Skills
* **`skills`** (List of Objects, Optional): 
  * Binds custom skills from MMO Mechanics to the mob.
  * Fields:
    * `skill` (String): The skill registration key matching the filename in MMO Mechanics (e.g. `fire_breath`).
    * `trigger` (String): The event that casts the skill:
      * `onAttack`: Casts when the mob hits another entity.
      * `onDamaged`: Casts when the mob receives damage.

### 5. Equipment
* **`equipment`** (Object, Optional): 
  * Equipment slots mapping. Resolves items from registered providers via YueMiLibs `ItemsApi` using namespace syntax (`namespace:itemId`).
  * Fields:
    * `hand` (String, Optional): Main hand weapon/item (e.g., `mmoitems:fire_sword`).
    * `offhand` (String, Optional): Offhand item/shield.
    * `helmet` (String, Optional): Helmet armor slot (e.g., `minecraft:golden_helmet`).
    * `chestplate` (String, Optional): Chestplate slot.
    * `leggings` (String, Optional): Leggings slot.
    * `boots` (String, Optional): Boots slot.

---

## Example Configuration (`fire_zombie.json5`)

```json5
{
  // Display name above the head
  name: "<red>Fire Zombie",
  
  // Base minecraft entity type
  type: "ZOMBIE",
  
  // Attributes settings
  health: 60,
  speed: 0.23,
  
  // Custom scoreboard tags
  tags: ["fire", "elite"],
  
  // Bound active triggers
  skills: [
    {
      skill: "fire_breath",
      trigger: "onAttack"
    },
    {
      skill: "speed_shield",
      trigger: "onDamaged"
    }
  ],
  
  // Equipment slot mappings
  equipment: {
    hand: "mmoitems:fire_sword",
    chestplate: "minecraft:iron_chestplate",
    leggings: "minecraft:iron_leggings",
    boots: "minecraft:iron_boots"
  }
}
```
