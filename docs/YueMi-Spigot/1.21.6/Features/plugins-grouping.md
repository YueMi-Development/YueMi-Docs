---
sidebar_position: 2
---
# Plugins Grouping
YueMi Spigot provides an extended plugin loading system.  
Unlike the default Paper/Spigot behavior, which only loads plugins from the `plugins/` directory, YueMi supports **multiple plugin directories** using a **wildcard folder system**.

## Plugin Folder Rules

- The **main plugin directory** must exist:
  - `plugins/`

- The system also recognizes **extra plugin directories**:
  - Any folder following the pattern `plugins-*`
  - Example:
    - `plugins-dev/`
    - `plugins-test/`
    - `plugins-extra/`

- All directory names are **case-insensitive** but are normalized to **lowercase** internally.

## Loading Order
When the server starts, the plugin system will:
1. Scan for all directories matching:
   - `plugins/`
   - `plugins-*`
2. Normalize folder names to lowercase.
3. Load plugins from each directory in that order.

Example usage:
```
plugins/
plugins-test/
plugins-libraries/
plugins-mmosets/
```

## Use Cases
This system allows:
- **Organized grouping**  
  Group plugins by function, e.g. `plugins-minigames/`, `plugins-essentials/`.

- **Safer testing**  
  Avoid confused when there are too many plugins inside one folder.

## Notes
- Plugins in different directories still share the same classloader rules as normal.  
- Duplicate plugins across folders may cause conflicts.  
- Always keep folder names lowercase for consistency.
- This Features is Experimental, some plugins may not support it.