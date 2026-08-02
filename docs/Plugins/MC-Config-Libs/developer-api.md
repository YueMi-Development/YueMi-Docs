---
sidebar_position: 4
title: Developer API
---

# Developer API

### `ConfigManager`

| Method | Description |
| :--- | :--- |
| `ConfigManager(JavaPlugin plugin, String scanPackage)` | Discovers all `MigrationStep` implementations in the given package. |
| `void loadAndMigrate(JavaPlugin plugin)` | Runs all pending migrations and saves `config.yml`. |

### `MigrationStep`

| Method | Description |
| :--- | :--- |
| `int getTargetVersion()` | The config version this step migrates **to**. |
| `void migrate(FileConfiguration config)` | Apply changes to the loaded configuration. |

---

## How Migration Versioning Works

```text
config-version: 1  →  MigrationV1ToV2 runs  →  config-version: 2
config-version: 2  →  MigrationV2ToV3 runs  →  config-version: 3
config-version: 3  →  (up to date, nothing runs)
```

Each step is applied only when `currentVersion == targetVersion - 1`, ensuring no step is skipped or applied twice.
