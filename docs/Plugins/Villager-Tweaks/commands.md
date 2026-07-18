---
sidebar_position: 2
title: Commands & Permissions
---

# Commands & Permissions

Villager Tweaks registers the `/villagertweaks` command (aliased as `/vt`) to manage plugin operations.

## Commands

| Command | Description | Permission |
| :--- | :--- | :--- |
| `/vt help` | Displays a list of available subcommands. | `villagertweaks.command.use` |
| `/vt reload` | Reloads the configuration file and applies migrations. | `villagertweaks.command.reload` |

## Base Permissions

- `villagertweaks.command.use`: Grants access to basic commands (default: true).
- `villagertweaks.command.reload`: Grants access to reload command (default: op).
