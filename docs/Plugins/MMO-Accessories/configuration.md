---
sidebar_position: 2
title: Configuration
---

# Configuration

The main configuration file is at `plugins/MmoAccessories/config.yml`. The shipped default ships at `config-version: 5`. Configuration is migrated forward by the built-in `MC-Config-Libs` migrator.

```yaml
# Do not change this version!
config-version: 5

# Storage backend for accessory data.
# Options: pdc (default), sqlite, mysql, mongodb
storage:
  type: pdc
  sqlite:
    file: "accessories.db"
  mysql:
    host: "localhost"
    port: 3306
    database: "minecraft"
    username: "root"
    password: ""
    pool-size: 10
  mongodb:
    uri: "mongodb://localhost:27017"
    database: "minecraft"
    collection: "accessories"

# Each slot type has:
#   display-name: Display name shown in GUI
#   max-slots:     Number of accessory slots for this type
#   accepted-types: List of types any-of matching
#   gui:
#     slots:       Inventory slot positions for the actual accessory slots
#     icon:        Material key for the empty-slot placeholder
#     label-name:  MiniMessage display name for the empty slot
#     label-lore:  MiniMessage lore lines for the empty slot
slots:
  BELT:
    display-name: "Belt"
    max-slots: 1
    accepted-types: ["BELT", "WAIST"]
    gui:
      slots: [20]
      icon: "minecraft:light_gray_stained_glass_pane"
      label-name: "<gold><bold>Belt Slot</bold></gold>"
      label-lore:
        - "<gray>Type: <green>BELT</green></gray>"
  RING:
    display-name: "Ring"
    max-slots: 2
    accepted-types: ["RING"]
    gui:
      slots: [30, 32]
      icon: "minecraft:yellow_stained_glass_pane"
      label-name: "<yellow><bold>Ring Slots</bold></yellow>"
      label-lore:
        - "<gray>Type: <green>RING</green></gray>"
  # ... GLOVES, NECKLACE, plus your own custom slots
```

## Storage Backends

| `storage.type` | Class | Notes |
| :--- | :--- | :--- |
| `pdc` (default) | `PdcStorage` | Stores accessory item ids in the player's `PersistentDataContainer`. Zero-config. |
| `sqlite` | `SqliteStorage` | Local file. `storage.sqlite.file` controls the path. |
| `mysql` | `MySqlStorage` | Connection pool. Credentials under `storage.mysql.*`. |
| `mongodb` | `MongoStorage` | URI + database + collection. |

Each optional backend's library is `compileOnly` in the build script so unused backends don't bloat the jar.

## Custom Slots

Add a new entry under `slots:` to define your own slot type (e.g. `CAPE`, `BELT_Buckle`):

```yaml
slots:
  CAPE:
    display-name: "Cape"
    max-slots: 1
    accepted-types: ["CAPE", "BACK"]
    gui:
      slots: [38]
      icon: "minecraft:black_stained_glass_pane"
      label-name: "<dark_purple><bold>Cape Slot</bold></dark_purple>"
      label-lore:
        - "<gray>Type: <green>CAPE</green></gray>"
```

Custom slot ids are accepted as-is; the API surface (`AccessorySlotId`) treats anything beyond the four built-in slots as a custom id.
