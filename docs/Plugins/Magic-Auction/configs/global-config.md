---
sidebar_position: 1
title: Global Configuration
---

# Global Configuration

The global configuration for Magic Auction is stored in `config.yml` under the plugin folder (`plugins/MagicAuction/config.yml`). It controls matchmaking settings, container preview blocks, bidding GUI sounds, and reveal animation parameters.

---

## Default Configuration

```yaml
# MagicAuction Configuration
# Do not change the config-version value manually.
config-version: 5

# Matchmaking settings
matchmaking:
  # Whether the matchmaking system is enabled globally.
  # When false, players cannot use /matchmaking join.
  enabled: true

  # Minimum number of real players required before a queue can start.
  min-players: 4

  # Seconds to wait for the queue to fill before taking action (see on-timeout).
  timeout-seconds: 120

  # Whether to fill remaining slots with bots when the timeout is reached.
  # Only used when on-timeout is "fill_bots".
  allow-bots: true

  # What action to take when the queue timeout is reached without enough players.
  # "fill_bots" — fill remaining slots with bots and start the auction
  # "cancel"   — cancel the queue and notify waiting players
  on-timeout: "fill_bots"

# Container preview & reveal settings
container:
  preview:
    # Material used for the full-size placeholder when an item's size is known
    # but nothing else has been revealed.
    # Accepts any Bukkit Material name.
    placeholder_pane: "IRON_BARS"

    # Material used for the 1x1 placeholder when rarity is known
    # but the item's size is still unknown.
    # Accepts any Bukkit Material name.
    placeholder_block: "GLASS"

  bid:
    # Sound events played during bidding
    sounds:
      # Played to the bidder when they successfully place a bid.
      # Accepts a Minecraft namespaced sound key.
      success: "minecraft:entity.villager.trade"

      # Played when a player closes the anvil without placing a bid.
      # Accepts a Minecraft namespaced sound key.
      cancel: "minecraft:entity.villager.no"

      # Played when a player's bid is invalid (format error, zero, or exceeds balance).
      # Accepts a Minecraft namespaced sound key.
      invalid: "minecraft:entity.villager.angry"

  reveal:
    # Whether the container reveal system is enabled globally.
    # When false, the winner reveal animation is skipped entirely.
    enabled: true

    # Whether to play the flicker animation during item reveals.
    # When false, items reveal one-by-one without the flicker effect.
    animation: true
```

---

## Configuration Properties

### Matchmaking Settings (`matchmaking`)

Matchmaking determines how players queue and how simulated bot players are filled.

| Field | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `enabled` | Boolean | `true` | Enables or disables the matchmaking queue system globally. If false, `/matchmaking join` will be disabled. |
| `min-players` | Integer | `4` | Minimum number of real players required in a queue to start an auction. |
| `timeout-seconds` | Integer | `120` | How long (in seconds) the queue will wait to fill before executing the `on-timeout` action. |
| `allow-bots` | Boolean | `true` | Allows filling empty slots with bots when the queue timeout is reached. |
| `on-timeout` | String | `"fill_bots"` | Action taken when the timeout is reached. <br/>- `"fill_bots"`: Fills slots with bots and starts.<br/>- `"cancel"`: Cancels queue and notifies players. |

### Container Preview Settings (`container.preview`)

Defines the appearance of placeholder items when items are masked/hidden in the auction preview phase.

| Field | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `placeholder_pane` | String | `"IRON_BARS"` | Material used for the item placeholder when the item's size (width/height) is known, but nothing else has been revealed. Accepts any Bukkit Material. |
| `placeholder_block` | String | `"GLASS"` | Material used for the item placeholder when the item's rarity is known, but its size is still unknown. Accepts any Bukkit Material. |

### Bidding GUI Sounds (`container.bid.sounds`)

Configures Minecraft namespaced sound keys played to players during the bidding phase.

| Field | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `success` | String | `"minecraft:entity.villager.trade"` | Sound played to the bidder when a bid is placed successfully. |
| `cancel` | String | `"minecraft:entity.villager.no"` | Sound played when a player closes the bidding anvil GUI without submitting a bid. |
| `invalid` | String | `"minecraft:entity.villager.angry"` | Sound played when a player's bid is invalid (e.g. format error, zero, or exceeds balance). |

### Winner Reveal Settings (`container.reveal`)

Controls the animation behavior when the auction ends and the winning container's contents are revealed.

| Field | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `enabled` | Boolean | `true` | Globally enables or disables the reveal phase. When false, the winner reveal animation is skipped entirely. |
| `animation` | Boolean | `true` | Enables or disables the suspenseful flicker animation during item reveals. If false, items reveal sequentially without the flicker effect. |
