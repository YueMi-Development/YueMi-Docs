---
sidebar_position: 1
title: "Reward Types"
---

# Reward Types

Bingo Gacha supports several reward types that can be configured under the `rewards` or `unused-point-rewards` sections of your card configurations.

---

## Economy Reward (`economy`)

Distributes currency directly to the player's account.

```yaml
- type: economy
  amount: 1000.0
```

### YueMi Libs Integration
* **Unified Economy**: If **YueMi Libs** is installed and enabled, the reward is automatically processed through the active economy provider configured in YueMi Libs (such as PlayerPoints, custom economies, etc.).
* **Vault Fallback**: If YueMi Libs is not present or no active provider is set, the plugin safely falls back to depositing via the standard **Vault** economy hook.

---

## Command Reward (`command`)

Executes one or more console commands on behalf of the player.

```yaml
- type: command
  command: "give %player% gold_ingot 3"
```

* **Placeholders**: Use `%player%` to reference the name of the player who completed the card.
* **Execution**: Executed safely asynchronously on the main thread via the console sender.

---

## Standard Item Reward (`item`)

Gives standard Minecraft items to the player with optional custom naming and lore.

```yaml
- type: item
  material: DIAMOND_SWORD
  amount: 1
  name: "<aqua>Excalibur"
  lore:
    - "<gray>A legendary sword of myth."
    - "<gold>Very sharp!"
```

* **Material**: Must be a valid Spigot/Bukkit `Material` name.
* **Name & Lore**: Supports Adventure MiniMessage formatting for colors and formatting tags (e.g. `<aqua>`, `<gold>`, `<gray>`).
* **Inventory Full Handling**: If the player's inventory is full, any leftover items will automatically drop naturally at the player's location.

---

## Custom Item Reward (`custom-item`)

Allows giving custom items from third-party plugins (e.g., CraftEngine, Nexo, ItemsAdder).

```yaml
- type: custom-item
  plugin: CraftEngine
  id: "my_namespace:sword_of_light"
  amount: 1
```

### YueMi Libs Integration
When YueMi Libs is present, all `custom-item` rewards are routed through its unified item management API:
1. **Namespace Wrapping**: The plugin lowercases the `plugin` name and prepends it to the item `id` as `plugin_name:item_id` (e.g. `craftengine:my_namespace:sword_of_light`).
2. **First-Colon Splitting**: YueMi Libs splits the key on the first colon to determine which plugin provider to call:
   * **Namespace**: `craftengine`
   * **Sub-Namespace / ID**: `my_namespace:sword_of_light`
3. **Provider Call**: The `CraftEngine` provider is called with `my_namespace:sword_of_light` and handles the sub-namespace matching internally to construct and give the item.

### Legacy Hook Fallback
If YueMi Libs is not installed or active, the plugin falls back to using direct reflection hooks to resolve the custom item via standard legacy APIs of supported plugins.
