---
sidebar_position: 7
---
# System
This Section Will Explaining About System Mechanism.

## Config Preview
```yaml
system:
  debugMode: true
  logLevel: 0
  licenseKeys: PUT-YOUR-LICENSE-HERE
  adaptiveTicking: true
  virtualThreads:
    useVirtualThreads: true
    vtAsyncExecutor: true
    vtAuthenticatorScheduler: true
    vtBukkitScheduler: true
    vtChatScheduler: false
    vtCommandBuilderScheduler: true
    vtProfileLookupScheduler: true
    vtServerTextFilterPool: true
    vtTabcompleteScheduler: true
  telemetry:
    enabled: true
    interval-minutes: 5
```

### Fields - System

- **debugMode**<br />
  Enables debug mode for detailed logging.
  > default: `true`

- **logLevel**<br />
  Defines the logging verbosity level.
  > default: `0`

- **licenseKeys**<br />
  The license key used to authenticate your server.
  > default: `PUT-YOUR-LICENSE-HERE`

- **adaptiveTicking**<br />
  Enables adaptive ticking to optimize server performance dynamically.
  > default: `true`

---

### Subfields - Virtual Threads
Configures how Java Virtual Threads (Project Loom) are utilized.

- **useVirtualThreads**<br />
  Enables the use of virtual threads overall.
  > default: `true`

- **vtAsyncExecutor**<br />
  Uses virtual threads for asynchronous task execution.
  > default: `true`

- **vtAuthenticatorScheduler**<br />
  Uses virtual threads for user authentication scheduler tasks.
  > default: `true`

- **vtBukkitScheduler**<br />
  Overrides standard Bukkit scheduler tasks with virtual threads.
  > default: `true`

- **vtChatScheduler**<br />
  Uses virtual threads for chat message processing.
  > default: `false`

- **vtCommandBuilderScheduler**<br />
  Uses virtual threads for command building.
  > default: `true`

- **vtProfileLookupScheduler**<br />
  Uses virtual threads for player profile lookup.
  > default: `true`

- **vtServerTextFilterPool**<br />
  Uses virtual threads for text filtering.
  > default: `true`

- **vtTabcompleteScheduler**<br />
  Uses virtual threads for tab completion.
  > default: `true`

---

### Subfields - Telemetry

- **enabled**<br />
  Enables telemetry data collection used locally for adaptive ticking.
  > default: `true`

- **interval-minutes**<br />
  Interval (in minutes) at which adaptive ticking telemetry data is processed.
  > default: `5`