---
sidebar_position: 2
title: Commands & Permissions
---

# Commands & Permissions

MMO Mobs registers the `/mmomobs` command (aliased as `/mobs`) for administrators.

## Commands

| Command | Description | Permission |
| :--- | :--- | :--- |
| `/mmomobs spawn <mobId> [amount]` | Spawn custom mobs at your target location. | `mmomobs.command.spawn` |
| `/mmomobs killall [mobId]` | Kill all custom mobs, optionally filtered by type. | `mmomobs.command.killall` |
| `/mmomobs reload` | Reload custom mob configuration files. | `mmomobs.command.reload` |

## Base Permissions

- `mmomobs.admin`: Grants access to all admin commands.
