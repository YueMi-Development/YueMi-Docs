---
sidebar_position: 2
title: RandomApi
---

# RandomApi

> Part of **YueMi-MC-Libs** · General Module

Hardware-seeded random generation backed by `java.security.SecureRandom` (OS-level entropy, not Java's pseudo-random `Random`).

## Why SecureRandom?

| | `SecureRandom` | `java.util.Random` |
|---|---|---|
| Entropy source | OS (e.g. `/dev/urandom`) | Seeded LCG algorithm |
| Predictable | No | Yes (given seed) |
| Performance | Slightly slower | Faster |
| Use case | Loot, gambling, rewards | Shuffling, non-critical |

Use `RandomApi` for anything where the outcome should not be predictable or reproducible — loot drops, mob rewards, gambling mechanics, etc.

## API Reference

```java
public class RandomApi {
    public static RandomApi getInstance();
    @NotNull SecureRandom secureRandom();       // underlying SecureRandom instance
    int nextInt(int bound);                     // [0, bound)
    double nextDouble();                        // [0.0, 1.0)
    boolean chance(double probability);         // true if nextDouble() < probability
    <T> @Nullable T pick(T @NotNull [] array);
    <T> @Nullable T pick(@NotNull List<T> list);
}
```

## Usage Examples

```java
RandomApi random = api.getGeneral().getRandom();

// Boolean chance roll
if (random.chance(0.25)) {          // 25% chance
    player.sendMessage("You got lucky!");
}

// Pick random element
String item = random.pick(List.of("sword", "shield", "potion"));

// Random number in range
int roll = random.nextInt(6) + 1;   // 1d6
```
