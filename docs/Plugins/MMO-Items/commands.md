---
sidebar_position: 2
title: Commands & Permissions
---

# Commands & Permissions

MMO Items registers the `/mmoitems` command (aliased as `/items`) for administrators.

## Commands

| Command | Description | Permission |
| :--- | :--- | :--- |
| `/mmoitems give <player> <itemId> [amount]` | Give a custom item to a target player. | `mmoitems.command.give` |
| `/mmoitems list` | List all registered custom items. | `mmoitems.command.list` |
| `/mmoitems reload` | Reload custom item configuration files dynamically. | `mmoitems.command.reload` |

## Base Permissions

- `mmoitems.admin`: Grants access to all admin commands.
