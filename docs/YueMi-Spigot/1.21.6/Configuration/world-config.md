---
sidebar_position: 5
---
# Worlds
Customize Worlds Related Features.

## Config Preview
```yaml
world:
  tnt:
    enableTNTOptimizations: true
    disableBlockDamage: false
    explosionRandomRange: -1.0
  allowSignColoring: true
  rightClickEditSign: false
  betterMending: true
  optimizePrecipitation: true
  optimizeChunkHolders: true
  optimizeMinecarts: true
  optimizeSuffocation: true
  regionizedChunkTicking:
    enableRegionizedChunkTicking: false
    executorThreadCount: 4
    executorThreadPriority: 7
  entityLoadChunks:
    tntLoadChunks: false
    fallingBlocksLoadChunks: false
    enderpearlsLoadChunks: false
    tridentsLoadChunks: false
```

### Fields - World
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

### Subfields - Regionized Chunk Ticking
Settings for the Regionized Chunk Ticking system.

- **enableRegionizedChunkTicking**<br />
  Enables the regionized chunk ticking system for performance improvements.  
  > default: `false`

- **executorThreadCount**<br />
  Number of threads allocated to process regionized chunks.  
  > default: `4`

- **executorThreadPriority**<br />
  Thread priority for regionized chunk tick execution.  
  > default: `7` (Thread.NORM_PRIORITY + 2)

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
