---
sidebar_position: 3
---
# Mobs
Customize Mobs Related Features.

## Config Preview
```yaml
mob:
  entityCollisions: false
  mobAI: true
  optimizeMobs: true
  entities:
    villager:
      lobotomizeVillager: false
      lobotomizeVillagerTickInterval: 20
      lobotomizeVillagerWaitUntilTradeLocked: true
      refresh-trades:
        interval: 12000
        random: 0
        night-refresh: false
      sounds:
        enabled: true
      celebration:
        enabled: true
      optimized-job-site-detection: true
```

### Fields - Mobs
- **entityCollisions**<br />
  Disables entity-to-entity collision calculations.
  > default: `false`

- **mobAI**<br />
  Controls whether mob AI is enabled globally.
  > default: `true`

- **optimizeMobs**<br />
  Enables various internal performance improvements.
  > default: `true`

---

### Subfields - Entities -> Villager
Specific optimizations and behavior controls for villagers.

- **lobotomizeVillager**<br />
  Disables pathfinding for villagers to save CPU cycles.
  > default: `false`

- **lobotomizeVillagerTickInterval**<br />
  How often (in ticks) to check and search pathfinding for lobotomized villagers.
  > default: `20`

- **lobotomizeVillagerWaitUntilTradeLocked**<br />
  If `true`, villagers will not be lobotomized until their trades are locked.
  > default: `true`

- **refresh-trades.interval**<br />
  Interval (in ticks) for refreshing trades.
  > default: `12000`

- **refresh-trades.random**<br />
  Random delay added to trade refresh.
  > default: `0`

- **refresh-trades.night-refresh**<br />
  Allows trade refreshes during the night.
  > default: `false`

- **sounds.enabled**<br />
  Enables or disables villager sounds.
  > default: `true`

- **celebration.enabled**<br />
  Enables or disables villager celebration behaviors (e.g. hero of the village).
  > default: `true`

- **optimized-job-site-detection**<br />
  Optimizes villager job site / POI searching algorithm.
  > default: `true`