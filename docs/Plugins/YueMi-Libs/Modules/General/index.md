---
sidebar_position: 1
title: General Module
---

# General Module

> Part of **YueMi-MC-Libs**

Utility APIs for formatting, comparison, random generation, and cascading drop systems.

## APIs

| API | Description |
|-----|-------------|
| [RandomApi](./RandomApi) | Hardware-seeded random, chance rolls, random picks |
| [CascadingDropSystem](./CascadingDropSystem) | Tiered rarity loot tables with direction support |
| CompareApi | ItemStack equality and similarity comparison |
| FormatApi | Number, duration, and percent formatting |

## GeneralApi

```java
public interface GeneralApi {
    @NotNull CompareApi getCompare();
    @NotNull FormatApi getFormat();
    @NotNull RandomApi getRandom();
}
```

## CompareApi

Compares two `ItemStack` objects for equality and similarity.

```java
public class CompareApi {
    public static CompareApi getInstance();
    @NotNull ItemComparison compare(@Nullable ItemStack item1, @Nullable ItemStack item2);
}

public record ItemComparison(
    boolean areEqual,
    boolean similar,
    boolean sameMaterial,
    boolean sameAmount,
    boolean sameDurability,
    boolean sameMeta,
    boolean sameEnchantments,
    boolean sameCustomModelData,
    @Nullable String differenceReason
) {
    public static ItemComparison equal();
    public static ItemComparison similar(@NotNull String reason);
    public static ItemComparison different(@NotNull String reason);
}
```

**Comparison levels:**

- **Equal** — same material, amount, durability, metadata, enchantments, and CustomModelData
- **Similar** — same material, amount, and enchantments (ignores metadata/durability differences)
- **Different** — anything that doesn't match above

```java
ItemComparison result = api.getGeneral().getCompare().compare(item1, item2);
if (result.areEqual()) {
    // exact match
} else if (result.similar()) {
    player.sendMessage("Difference: " + result.differenceReason());
}
```

## FormatApi

```java
public class FormatApi {
    public static FormatApi getInstance();

    @NotNull String formatNumber(long number);      // "1,234,567"
    @NotNull String formatDecimal(double number);  // "1,234.57"
    @NotNull String formatCompact(long number);    // "1.5M", "2.3K", "500"
    @NotNull String formatDuration(long seconds);  // "2h 30m", "45s"
    @NotNull String formatPercent(double value);   // "75.5%"
}
```

**Examples:**

| Input | Method | Output |
|-------|--------|--------|
| `1500000` | `formatCompact` | `"1.5M"` |
| `3665` | `formatDuration` | `"1h 1m"` |
| `0.755` | `formatPercent` | `"75.5%"` |
| `1234567` | `formatNumber` | `"1,234,567"` |
| `1234.567` | `formatDecimal` | `"1,234.57"` |
