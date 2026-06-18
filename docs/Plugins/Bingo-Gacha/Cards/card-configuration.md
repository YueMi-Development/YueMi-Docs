---
sidebar_position: 1
title: "Card Configuration"
---

# Card Configuration Guide

Bingo Gacha configurations are structured inside the `cards/` directory. Each `.yml` file in this directory represents a standalone gacha card template.

---

## Layout & Base Properties

```yaml
# Title of the GUI card inventory
title: "<gold>★ Mini Bingo Gacha ★"

# Grid size of the card: either '3x3' or '5x5'
size: 3x3

# If true, players can claim and start this card again once completed
repeatable: true

# The completion rule required:
# - STRAIGHT_LINE: completes when any line (horizontal, vertical, diagonal) is filled
# - FULL_CARD: completes only when every single slot is unlocked
completion-type: STRAIGHT_LINE

# If true, players can purchase this card from the shop GUI
buyable: true
```

---

## Cost Configurations

Cards support both **Vault economy** cost and **Item** cost.

### Vault (Economy) Cost
```yaml
buy-cost:
  type: vault
  amount: 500.0

roll-cost:
  type: vault
  amount: 100.0
```

### Item Cost
```yaml
buy-cost:
  type: item
  material: EMERALD
  amount: 10

roll-cost:
  type: item
  material: GOLD_INGOT
  amount: 5
```

---

## Rewards

Rewards are divided into `rewards` (granted upon card completion) and `unused-point-rewards` (granted for each unrolled slot when completing with the `STRAIGHT_LINE` rule).

Supported reward types:
*   `economy`: Vault money
*   `command`: Console commands executed for the player (supports `%player%`)

```yaml
rewards:
  - type: economy
    amount: 1000.0
  - type: command
    command: "give %player% gold_ingot 3"

# Commiseration / extra rewards for not having rolled these slots yet
unused-point-rewards:
  - type: economy
    amount: 50.0
```

---

## Slots Configuration

You must define items matching the grid slots (9 slots for `3x3`, 25 slots for `5x5` numbered `0` to `24`).

```yaml
slots:
  0:
    material: COAL
    name: "<gray>Coal Slot"
    lore:
      - "<gray>A dusty piece of coal."
  1:
    material: IRON_INGOT
    name: "<white>Iron Slot"
    lore:
      - "<gray>A shiny ingot of iron."
  # ... Add up to size requirement (e.g. 8 for 3x3, 24 for 5x5)
```
