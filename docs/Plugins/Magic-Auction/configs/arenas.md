---
title: Arena Configurations
sidebar_position: 2
---

# Arena Configuration

Arenas are configured under the `auction/` directory as individual YAML (`.yml`) files. They control the flow, timing, pricing multipliers, and prize pools of an auction session.

---

## Example Arena Config

```yaml
id: "arena1"
name: "Golden Mystery Arena"
thinking-time: 15
bid-time: 30
base-price: 100
min-items: 5
max-items: 8
multipliers:
  - 2.0
  - 1.5
  - 1.3
  - 1.1
  - 1.0
events:
  - "reveal_all_common"
  - "reveal_one_type_random"
  - "reveal_one_size_random"
  - "reveal_three_types"
  - "reveal_two_sizes"
rewards:
  - id: "golden_ticket"
    amount: 3
  - id: "magic_dust"
    amount: 5
  - id: "lucky_charm"
    amount: 2
  - id: "coal_lump"
    amount: 3
```

---

## Configuration Properties

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `id` | String | *Required* | Unique identifier for the arena. Must match the filename. |
| `name` | String | *Required* | Display name of the arena. |
| `thinking-time` | Integer | 15 | Preview countdown duration in seconds. |
| `bid-time` | Integer | 30 | Bidding phase duration in seconds before timeout (defaults bid to $1). |
| `base-price` | Double | 100.0 | Base price floor used for BIN calculations if only one player bids. |
| `min-items` | Integer | 5 | Minimum number of items selected from the reward pool to populate the preview chest. |
| `max-items` | Integer | 8 | Maximum number of items selected from the reward pool. |
| `multipliers` | List of Doubles | — | List of multipliers for each round. The size of this list determines the number of rounds in the game. Multipliers are clamped between `1.0` and `10.0` at runtime. |
| `events` | List of Strings | — | A list of round event config IDs. Shuffled deterministically at the start of the session. |
| `rewards` | List | — | List of custom items and their maximum quantities in the pool. |
| `start-events` | Integer | 0 | Number of events to execute at the start of Round 1 before the preview opens. |
