---
sidebar_position: 2
title: AI & Goal Selectors
---

# AI & Goal Selectors

You can customize mob pathfinding and targeting behaviors using the `AIGoalSelectors` configuration list. This allows you to clear standard AI behaviors and register specific actions with custom priorities.

---

## Configuration Syntax

Goal selectors are defined under the `options` block of a mob configuration file as a list of strings:

```json5
{
  name: "Patrol Guard",
  type: "ZOMBIE",
  health: 40,
  options: {
    AIGoalSelectors: [
      "0 clear",
      "1 patrol 10,64,10;20,64,20;30,64,10",
      "2 lookatplayers",
      "3 float"
    ]
  }
}
```

- **Priority Prefix**: The number prefix (e.g. `1 ` in `1 patrol ...`) specifies the priority of the goal. Lower numbers indicate higher priority.
- **Parameters**: Some custom goals take parameters following their name (e.g., coordinates, distances, or speeds).

---

## Supported AI Goals

### General / Vanilla Goals
These control vanilla Minecraft behaviors. Mobs can only use these goals if their vanilla entity type supports them naturally.

| Goal Name / Alias | Description |
| :--- | :--- |
| `clear` / `reset` | Removes all existing AI goals from the mob. |
| `float` / `swim` | Makes the mob swim/float in water. |
| `lookatplayers` | Makes the mob look at nearby players. |
| `lookattarget` | Makes the mob look at its current target. |
| `randomlookaround` / `lookaround` | Makes the mob randomly look around. |
| `opendoor` / `opendoors` | Allows the mob to open doors it runs into. |
| `breakdoors` | Allows the mob to break down doors it runs into. |
| `eatgrass` | Makes the mob occasionally eat grass (Sheep behavior). |
| `meleeattack` | Basic melee attack behavior. |
| `zombieattack` | Zombie-specific melee attack behavior. |
| `spiderattack` | Spider-specific pouncing attack behavior. |
| `leapattarget` | Makes the mob leap/pounce at its target. |
| `breed` | Allows the mob to breed. |
| `panic` | Runs around frantically when set on fire. |
| `creeperswell` / `creeperexplode` | Creeper-specific explosion countdown behavior. |
| `rangedattack` / `arrowattack` | Basic ranged projectile attack. |
| `bowattack` / `bowshoot` / `bowmaster` | Advanced skeleton-style bow attack behavior. |
| `crossbowattack` | Crossbow ranged attack behavior. |

---

## Custom AI Goals
These goals are implemented directly by the plugin and can be configured with arguments:

### 1. `gotolocation` (or `goto`)
Forces the mob to pathfind to a specific location coordinate:
- **Format**: `gotolocation <x>,<y>,<z>[,speed]`
- **Example**: `1 gotolocation 100,64,100,1.2`

### 2. `gotoowner`
Instructs the mob to pathfind to its owner when it wanders further than a threshold:
- **Format**: `gotoowner [minDistance] [speed]`
- **Example**: `1 gotoowner 5 1.0` (Defaults to 5 blocks distance minimum)

### 3. `patrol` (or `patrolroute`)
Sets up a sequential path for the mob to patrol between multiple coordinates:
- **Format**: `patrol <x1>,<y1>,<z1>;<x2>,<y2>,<z2>;...`
- **Example**: `1 patrol 10,64,10;20,64,20;30,64,10`

### 4. `fleeplayers` (or `runfromplayers`)
Forces the mob to run away from nearby players within a specified radius:
- **Format**: `fleeplayers [radius] [speed]`
- **Example**: `1 fleeplayers 12 1.3`

### 5. `donothing`
Halts all pathfinding, targeting, and movement behaviors for the mob:
- **Format**: `donothing`
- **Example**: `0 donothing`
