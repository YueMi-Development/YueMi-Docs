---
sidebar_position: 2
title: Example Usage
---

# Example Usage

This guide walks you through a complete example of migrating a configuration key. We will migrate a setting `old-key` (version 1) to `new-key` (version 2).

### Step 1: Define the Config Version

Add a version key to your plugin's default `config.yml` (located in `src/main/resources`). This specifies the version for new installs.

```yaml
# config.yml
config-version: 2

# The new setting key
new-key: "default-value"
```

### Step 2: Implement the Migration Step

Create a migration class under your migrations package (e.g. `org.yuemi.myplugin.config.migrations`). It must implement the `MigrationStep` interface:

```java
package org.yuemi.myplugin.config.migrations;

import org.bukkit.configuration.file.FileConfiguration;
import org.yuemi.config.api.MigrationStep;

/**
 * Migrates configuration from version 1 to 2.
 * This renames "old-key" to "new-key".
 */
public class MigrationV1ToV2 implements MigrationStep {

    @Override
    public int getTargetVersion() {
        return 2; // Target version of this migration step
    }

    @Override
    public void migrate(FileConfiguration config) {
        // 1. Retrieve the existing value
        String value = config.getString("old-key");
        
        // 2. Set the new key with the old value
        config.set("new-key", value);
        
        // 3. Remove the old key
        config.set("old-key", null);
    }
}
```

### Step 3: Initialize the ConfigManager

In your main plugin class, initialize the `ConfigManager` and run the migration in `onEnable()`:

```java
package org.yuemi.myplugin;

import org.bukkit.plugin.java.JavaPlugin;
import org.yuemi.config.api.ConfigManager;

public class MyPlugin extends JavaPlugin {

    private ConfigManager configManager;

    @Override
    public void onEnable() {
        // Point the manager to the package containing all migration classes
        configManager = new ConfigManager(this, "org.yuemi.myplugin.config.migrations");
        
        // Load default config and apply migrations
        configManager.loadAndMigrate(this);
    }
}
```
