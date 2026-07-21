---
title: Round Events
sidebar_position: 3
---

# Round Events Configuration

Round Events occur at the start of rounds (or at the very start of the auction session if configured in `start-events`). They reveal information about the masked preview container items, allowing players to make informed bids.

Events are configured in the `events/` folder as individual YAML (`.yml`) files.

---

## Example Event Configs

### 1. Rarity Condition Reveal
```yaml
name: "Common Exposure"
desc: "All common items are fully revealed!"
actions:
  - type: "full"
    selection: "all"
    count: 0
    rarity: "common"
```

### 2. Random Selection with Rarity Condition
```yaml
name: "Reveal Five Rare"
desc: "Reveal 5 items that have rarity rare"
actions:
  - type: "full"
    selection: "random"
    count: 5
    conditions:
      rarity: "rare"
```

---

## Action Configurations

An event config is composed of a `name`, `desc` (description), and a list of `actions` to run.

Each action supports the following fields:

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `type` | String | *Required* | The reveal type to apply: <br/>- `"type"`: Reveals only the item's custom type.<br/>- `"rarity"`: Reveals only the item's rarity.<br/>- `"size"`: Reveals only the item's layout size (width/height).<br/>- `"full"`: Fully reveals the item stack details. |
| `selection` | String | `"random"` | The selection strategy: <br/>- `"random"`: Randomly picks items up to the configured `count`. <br/>- `"all"`: Applies to all matching items. |
| `count` | Integer | 0 | The number of items to reveal when using `"random"` selection. |
| `rarity` | String | — | Legacy shorthand condition for filtering by rarity ID. |
| `conditions` | Map | — | Conditional rules to filter items. Supports: <br/>- `rarity`: String rarity ID filter. <br/>- `min-total-size`: Minimum grid space size filter (width × height). |
