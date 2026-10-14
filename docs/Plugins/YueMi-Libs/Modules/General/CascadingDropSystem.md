---
sidebar_position: 3
title: Cascading Drop System
---

# Cascading Drop System

> Part of **YueMi-MC-Libs** · General Module

Tiered rarity drop system — tiers are evaluated in order, and a second roll determines which item within the hit tier is dropped. Optionally guarantees a drop via a fallback list.

## Core Concepts

| Concept | Description |
|---------|-------------|
| **Rarity tier** | A group of items sharing the same drop chance, opened via `addRarity(chance)` |
| **Tier direction** | The order in which tiers are checked: `LOW_TO_HIGH` or `HIGH_TO_LOW` |
| **Item weight** | Relative probability within a tier, set via `withDrop(item, chance)` |
| **Fallback** | Guaranteed drop when all tiers miss, set via `mustHaveSome(list)` |

## How It Works

1. Evaluate tiers in configured direction
2. For each tier: roll `chance()` — if miss, continue to next tier
3. If tier hits: roll for an item within that tier using item weights
4. If tier hits but no item selected (weights sum < 1.0): cascade to next tier
5. After all tiers: use fallback if set, otherwise return `null`

## CascadeDirection

Controls which tier is evaluated first.

| Direction | Check order | Best for |
|---|---|---|
| `LOW_TO_HIGH` | Tier 0 → last | Common loot tables, farming |
| `HIGH_TO_LOW` | Last → Tier 0 | Gacha, boss drops, rarity-first |

## Quick Start

```java
RandomApi random = api.getGeneral().getRandom();

CascadingDropSystem<Material> drops =
    CascadingDropBuilder.<Material>create(random)
        .direction(CascadeDirection.LOW_TO_HIGH)
        // Tier 0 — Common (50%)
        .addRarity(0.50)
        .withDrop(Material.DIRT, 1.0)
        // Tier 1 — Rare (20% of remaining rolls)
        .addRarity(0.20)
        .withDrop(Material.GOLD_INGOT, 0.7)
        .withDrop(Material.DIAMOND, 0.3)
        // Tier 2 — Legendary (5% of remaining rolls)
        .addRarity(0.05)
        .withDrop(Material.NETHERITE_INGOT, 1.0)
        .mustHaveSome(List.of(Material.COAL))  // guaranteed fallback
        .build();

// In a mob death event:
Material drop = drops.roll();
if (drop != null) {
    event.getDrops().add(new ItemStack(drop));
}
```

## Effective Probabilities

With `LOW_TO_HIGH` direction and tiers at 50%, 20%, 5%:

| Outcome | Calculation | Rate |
|---|---|---|
| Common | 50% | 50.0% |
| Rare | (1-0.50) × 0.20 | 10.0% |
| Legendary | (1-0.50) × (1-0.20) × 0.05 | 2.0% |
| Fallback | (1-0.50) × (1-0.20) × (1-0.05) | 38.0% |
| **Total** | | **100%** |

Each `addRarity()` is a **conditional** chance — it only applies to rolls that survived all previous tiers.

## CascadeDirection Examples

### LOW_TO_HIGH — Common drops first

```java
// Checked: Common → Rare → Legendary
CascadingDropBuilder.<Material>create(random)
    .direction(CascadeDirection.LOW_TO_HIGH)
    .addRarity(0.50)         // Tier 0 — Common (checked first)
    .withDrop(Material.DIRT, 1.0)
    .addRarity(0.10)         // Tier 1 — Rare (checked second)
    .withDrop(Material.GOLD_INGOT, 1.0)
    .addRarity(0.02)          // Tier 2 — Legendary (checked last)
    .withDrop(Material.DIAMOND, 1.0)
    .build();
```

### HIGH_TO_LOW — Legendary drops first

```java
// Checked: Legendary → Rare → Common
CascadingDropBuilder.<Material>create(random)
    .direction(CascadeDirection.HIGH_TO_LOW)
    .addRarity(0.50)         // Tier 0 — Common (checked LAST)
    .withDrop(Material.DIRT, 1.0)
    .addRarity(0.10)         // Tier 1 — Rare (checked second)
    .withDrop(Material.GOLD_INGOT, 1.0)
    .addRarity(0.02)         // Tier 2 — Legendary (checked FIRST)
    .withDrop(Material.DIAMOND, 1.0)
    .build();
```

## Cascading Behavior

When a tier is hit but no item is selected (sum of item chances < 1.0), the cascade continues to the next tier — it does **not** fall through to the fallback immediately.

```java
// Tier 0 hits 100%, but items only sum to 70%
// → 30% chance to cascade to Tier 1
CascadingDropBuilder.<String>create(random)
    .addRarity(1.0)
    .withDrop("maybe", 0.5)          // 50% within tier
    .withDrop("also_maybe", 0.2)     // 70% total — 30% cascades
    .addRarity(1.0)                  // reached if Tier 0 didn't drop
    .withDrop("fallback_tier", 1.0)
    .build();
```
