---
title: Commands & Permissions
sidebar_position: 3
---

# Commands & Permissions

MC-MMO-Accessories registers the `/accessories` command (no alias) for administrators and players.

## Commands

| Command | Description | Permission | Sender |
| :--- | :--- | :--- | :--- |
| `/accessories open` | Open the player's own accessories GUI. | `accessories.command.open` | player |
| `/accessories reload` | Reload the plugin config from disk. | `accessories.command.reload` | any |
| `/accessories list <player>` | List a target's currently equipped accessories. | `accessories.command.list` | any |
| `/accessories view <player>` | Open another player's accessories GUI (admin view). | `accessories.command.view` | player |
| `/accessories wipe <player>` | Wipe a target's equipped accessories. | `accessories.command.wipe` | any |

## Base Permissions

- `accessories.feature` — gate the soft feature flag queried by `AccessoriesApi.isFeatureEnabled(player)`.
- `accessories.command.open` — open own GUI.
- `accessories.command.reload` — reload config.
- `accessories.command.list` — list a target's accessories.
- `accessories.command.view` — open another player's GUI.
- `accessories.command.wipe` — wipe a target's accessories.

## Sender Rules

- GUI-bound commands (`open`, `view`) require a player sender and refuse console execution.
- Pure admin commands (`reload`, `list`, `wipe`) accept either a player or the console sender.
