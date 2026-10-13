---
sidebar_position: 2
title: Configuration
---

# Configuration

The main configuration file is located at `plugins/YueMiLibs/config.yml`. It handles system-wide hooks and sets options for the standard providers. Per-feature modules also ship their own default configs (e.g. `module-gui`, `module-event`) which can override module-specific behaviour.

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

## Per-Feature Packages

YueMi Libs splits its public surface into per-feature packages under `org.yuemi.libs.api.*`. Each is shipped through the single `YueMiLibs-api` artifact:

- `org.yuemi.libs.api.gui` — `GuiApi`, `Gui`, `GuiLayer`, `GuiItem`, `SlotBehavior`, `GuiListener` helpers.
- `org.yuemi.libs.api.event` — `EventApi`, `EventProvider`, `BukkitEvents`, `PlayerEvents`, `EntityEvents`, `BlockEvents`.
- `org.yuemi.libs.api.items` — `ItemsApi` (ItemsAdder / CraftEngine / Nexo / vanilla namespaces).
- `org.yuemi.libs.api.economy` — `EconomyApi` (Vault bridge).

If you only need the items / economy surface you can disable the GUI and event modules in `plugin.yml`; YueMi Libs gracefully no-ops when its modules are not enabled.
