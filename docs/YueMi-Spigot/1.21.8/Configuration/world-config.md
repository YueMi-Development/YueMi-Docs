---
sidebar_position: 5
---
# Worlds
Customize Worlds Related Features.

## Config Preview
```yaml
world:
  optimizeTerrainGenerator: true
  allowSignColoring: true
  rightClickEditSign: true
  betterMending: true
  optimizePrecipitation: true
  optimizeChunkHolders: true
  optimizeMinecarts: true
  optimizeSuffocation: true
  perWorldTpsBar: true
  tnt:
    enableTNTOptimizations: true
    disableBlockDamage: false
    explosionRandomRange: -1.0
  entityLoadChunks:
    tntLoadChunks: false
    fallingBlocksLoadChunks: false
    enderpearlsLoadChunks: false
    tridentsLoadChunks: false
  asyncWorld:
    enableAsyncWorld: true
    usePerWorldTpsBar: true
    showTPSOfServerInsteadOfWorld: true
    parallelWorldTicking:
      enableParallelWorldTicking: true
      parallelThreadCount: 4
      logContainerCreationStackTraces: false
      disableHardThrow: false
      compatibilityMode: false
    chunkSending:
      maxThreads: 1
    regionizedChunkTicking:
      enableRegionizedChunkTicking: true
      executorThreadCount: 4
      executorThreadPriority: 7
```

### Fields - World
- **optimizeTerrainGenerator**<br />
  Optimizes the terrain generation algorithms to reduce CPU overhead.
  > default: `true`

- **allowSignColoring**<br />
  Allows players to use color codes on signs.  
  > default: `true`

- **rightClickEditSign**<br />
  Lets players right-click a sign to edit it instantly.  
  > default: `true`

- **betterMending**<br />
  Improves the behavior of the Mending enchantment.  
  > default: `true`

- **optimizePrecipitation**<br />
  Optimizes ice/snow detection and placement to reduce chunk scanning.  
  > default: `true`

- **optimizeChunkHolders**<br />
  Caches frequently accessed chunk holders for faster lookup.  
  > default: `true`

- **optimizeMinecarts**<br />
  Optimizes minecart physics, collision, and ticking logic.  
  > default: `true`

- **optimizeSuffocation**<br />
  Improves suffocation mechanics by reducing redundant hitbox checks.  
  > default: `true`

- **perWorldTpsBar**<br />
  Displays a TPS bossbar specific to each world.
  > default: `true`

---

### Subfields - TNT
Controls TNT behavior and optimizations.

- **enableTNTOptimizations**<br /> 
  Enables server-side TNT optimizations for better performance.  
  > default: `true`

- **disableBlockDamage**<br />
  If `true`, TNT explosions do not destroy blocks.  
  > default: `false`

- **explosionRandomRange**<br />
  Adds random variation to TNT explosion strength.  
  > default: `-1.0` (disabled)

---

### Subfields - Entity Load Chunks
Controls which entity types can force chunks to load.

- **tntLoadChunks**<br />
  Whether primed TNT can load chunks while moving.  
  > default: `false`

- **fallingBlocksLoadChunks**<br />
  Whether falling blocks (sand, gravel, anvils) load chunks.  
  > default: `false`

- **enderpearlsLoadChunks**<br />
  Whether thrown enderpearls load chunks mid-flight.  
  > default: `false`

- **tridentsLoadChunks**<br />
  Whether thrown tridents load chunks mid-flight.  
  > default: `false`

---

### Subfields - Async World
Optimizations for multi-threaded and async world features.

- **enableAsyncWorld**<br />
  Enables asynchronous world ticking/handling.
  > default: `true`

- **usePerWorldTpsBar**<br />
  Uses the per-world TPS bar with the async engine.
  > default: `true`

- **showTPSOfServerInsteadOfWorld**<br />
  Shows global server TPS instead of individual world TPS in the bar.
  > default: `true`

#### Parallel World Ticking
- **enableParallelWorldTicking**<br />
  Ticks multiple worlds in parallel threads.
  > default: `true`

- **parallelThreadCount**<br />
  Number of threads allocated for parallel world ticking.
  > default: `4`

- **logContainerCreationStackTraces**<br />
  Logs stack traces during container creation for debug purposes.
  > default: `false`

- **disableHardThrow**<br />
  Prevents severe exceptions from stopping the server.
  > default: `false`

- **compatibilityMode**<br />
  Enables legacy compatibility features for parallel ticking.
  > default: `false`

#### Chunk Sending
- **maxThreads**<br />
  Maximum threads allocated to chunk sending.
  > default: `1`

#### Regionized Chunk Ticking
- **enableRegionizedChunkTicking**<br />
  Enables the regionized chunk ticking system.  
  > default: `true`

- **executorThreadCount**<br />
  Number of threads allocated to process regionized chunks.  
  > default: `4`

- **executorThreadPriority**<br />
  Thread priority for regionized chunk tick execution.  
  > default: `7`
