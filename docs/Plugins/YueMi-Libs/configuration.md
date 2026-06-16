---
sidebar_position: 2
title: Configuration
---

# Configuration

The main configuration file is located at `plugins/YueMiLibs/config.yml`. It handles system-wide hooks and sets options for standard providers.

Here is the default configuration file for **version 3**:

```yaml
# YueMi Libs Configuration

# Do not change this version!
config-version: 3

# Configure third-party hooks and integration
hooks:
  economy:
    enabled: true
    # The economy provider to hook (e.g. "Vault")
    provider: "Vault"
  items:
    # Whether to hook into CraftEngine to support its custom items
    craftengine:
      enabled: true

# Configuration for item providers
providers:
  minecraft:
    # How strictly to match items when checking or taking them from player inventories.
    # Options:
    # - ID: Matches only by Material ID type (e.g. minecraft:stone)
    # - CUSTOM_MODEL_DATA: Matches by Material ID type and Custom Model Data
    # - NBT: Matches strictly (all metadata / NBT must match)
    match-mode: "ID"
```

---

## Configuration Options

### `hooks.economy`
*   `enabled` (Boolean): Set to `true` to enable hooking into economy plugins.
*   `provider` (String): The economy system to hook. Currently supports `"Vault"`.

### `hooks.items.craftengine`
*   `enabled` (Boolean): Set to `true` to hook into the **CraftEngine** plugin when available on the server. This exposes the `craftengine:` namespace to the items API.

### `providers.minecraft.match-mode`
Configures how strictly the default vanilla item provider matches items when checking (`getItemCount`) or removing (`takeItem`) them from player inventories:

| Match Mode | Description |
| :--- | :--- |
| `ID` | Matches only the material type (e.g., matching `minecraft:stone` matches any stone blocks, ignoring NBT, names, lore, or model data). |
| `CUSTOM_MODEL_DATA` | Matches the material type AND Custom Model Data. E.g., matching a sword with custom model data `101` will ignore swords with model data `102` or no model data. |
| `NBT` | Matches strictly using Bukkit's `.isSimilar()` comparison, requiring all names, lore, enchantments, and tag metadata to be identical. |
