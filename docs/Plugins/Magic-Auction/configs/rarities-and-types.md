---
title: Rarities and Types
sidebar_position: 5
---

# Rarities & Types Configurations

Rarities and Types define the classification of mystery items. They are used for grid masking colors, hover lores, and event reveal filters.

---

## Rarities Configuration

Rarities are configured in the `rarities/` directory.

### Example Rarity (`legendary.yml`)
```yaml
name: "Legendary"
description: "A legendary treasure!"
color: "orange"
reveal-sounds:
  - "minecraft:entity.player.levelup"
  - "minecraft:ui.toast.challenge_complete"
```

### Properties
* **`name`**: Display name of the rarity (e.g., Common, Uncommon, Legendary).
* **`description`**: Brief description included in item lore.
* **`color`**: Adventure color tag name used to style the item's display elements (e.g., `gray`, `green`, `blue`, `purple`, `gold`, `orange`, `red`).
* **`reveal-sounds`**: (Optional) A list of Minecraft namespaced sound keys played when an item of this rarity is revealed during the Winner Reveal phase.
  
> [!WARNING]
> Rarity configuration files cannot use the color `black` as a valid color value. The color `black` is reserved for unknown/masked states in the preview GUI.

---

## Types Configuration

Types categorize items and are configured in the `types/` directory.

### Example Type (`collectible.yml`)
```yaml
name: "Collectible"
description: "Rare item for showcasing or trading"
```

### Properties
* **`name`**: Display name of the item category (e.g., Material, Tool, Armor, Collectible).
* **`description`**: Description of what this category represents.
