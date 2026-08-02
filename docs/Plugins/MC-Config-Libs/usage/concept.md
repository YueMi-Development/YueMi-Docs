---
sidebar_position: 1
title: What is Migration
---

# What is Migration?

As you update your Minecraft plugins, you will inevitably need to modify the configuration structure (`config.yml`). You might want to rename a setting, move settings into nested sections, or delete obsolete options.

If you simply release a new plugin version with a new default configuration, existing servers running your plugin will face one of two problems:
1.  **Broken Features**: The plugin expects new configuration keys that don't exist in their older `config.yml`.
2.  **Overwritten Configurations**: The server administrator's customized options are overwritten by the new default configuration.

**Configuration Migration** is the automated process of upgrading an existing config file to a newer structure at startup, without losing the user's custom settings.

---

## The MC Config Libs Approach

Instead of writing complex, error-prone parser code to manually read, compare, and modify YAML values every time you release an update, **MC Config Libs** structures migration into discrete, incremental steps:

```text
User's Config (v1) ──► Apply Step 2 ──► Config (v2) ──► Apply Step 3 ──► Final Config (v3)
```

Each change is represented by a single Java class called a `MigrationStep`. When your plugin starts, the library:
1.  Reads the current version from the server's `config.yml`.
2.  Discovers all compiled `MigrationStep` classes in your plugin.
3.  Determines which migrations are missing.
4.  Applies the missing steps in order.
5.  Saves the updated configuration.
