---
title: Commands
sidebar_position: 2
---

# Commands & Permissions

Magic Auction provides commands for starting auctions, joining matchmaking queues, and administrative functions.

---

## Subcommands of `/magicauction`

The base admin command is `/magicauction` (aliases: `/ma`).

### `/magicauction start <arena> [seed] <p1> <p2> <p3> <p4>`
* **Description**: Starts an auction session manually in the specified arena with 4 players.
* **Arguments**:
  * `<arena>`: The ID of the arena config (e.g. `arena1`).
  * `[seed]`: (Optional) An integer seed for deterministic generation. Set to `-1` or omit for random.
  * `<p1> <p2> <p3> <p4>`: The exact names of the 4 players. Use `_BOT_` to spawn simulated bot players (requires the bot module to be active).
* **Permission**: `magicauction.admin.start`
* **Example**: `/magicauction start arena1 12345 Player1 Player2 _BOT_ _BOT_`

### `/magicauction matchmaking <join|leave>`
* **Description**: Subcommand gateway for queue operations.
* **Permission**: `magicauction.player.matchmaking`

---

## Matchmaking Commands

Players can queue for auctions using `/matchmaking` (aliases: `/mm`).

### `/matchmaking join <arena>`
* **Description**: Joins the matchmaking queue for the specified arena.
* **Permission**: `magicauction.player.matchmaking`
* **Example**: `/matchmaking join arena1`

### `/matchmaking leave [arena]`
* **Description**: Leaves the matchmaking queue for the specified arena. If no arena is provided, leaves all active queues.
* **Permission**: `magicauction.player.matchmaking`
* **Example**: `/matchmaking leave arena1`
