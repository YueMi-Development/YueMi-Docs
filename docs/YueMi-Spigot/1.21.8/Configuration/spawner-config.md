---
sidebar_position: 2
---
# Spawners
Customize Custom Spawner System.

## Config Preview
```yaml
spawners:
  customSpawnerSystem: true
  redstoneDeactivates: true
  needPlayersNearby: true
  spawnerParticles: false
  spawnRadius: 4
  playerAFKRadius: 10
  spawnDelay: 20
  minimumSpawnTicks: 200
  maximumSpawnTicks: 600
  spawnCount: 4
  maxNearbyEntities: 6
```

- **customSpawnerSystem**<br />
  Enables YueMi’s optimized internal spawner logic.  
  > default: `true`

- **redstoneDeactivates**<br />
  Redstone signals disable the spawner.  
  > default: `true`

- **needPlayersNearby**<br />
  Spawner requires nearby players to activate.  
  > default: `true`

- **spawnerParticles**<br />
  Shows particle effects when the spawner is active.  
  > default: `false`

- **spawnRadius**<br />
  Horizontal radius around the spawner where mobs can spawn.  
  > default: `4`

- **playerAFKRadius**<br />
  Distance used to determine whether a player is considered AFK for spawning checks.  
  > default: `10`

- **spawnDelay**<br />
  Base delay (in ticks) before the next spawn attempt.  
  > default: `20`

- **minimumSpawnTicks**<br />
  Minimum interval (in ticks) between spawn cycles.  
  > default: `200`

- **maximumSpawnTicks**<br />
  Maximum interval (in ticks) between spawn cycles.  
  > default: `600`

- **spawnCount**<br />
  How many mobs the spawner attempts to generate each cycle.  
  > default: `4`

- **maxNearbyEntities**<br />
  If this many mobs already exist in range, the spawner pauses.  
  > default: `6`