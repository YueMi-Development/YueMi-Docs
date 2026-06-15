---
sidebar_position: 7
---
# System
This Section Will Explaining About System Mechanism.

## Config Preview
```yaml
system:
  useVirtualThread: true
  licenseKeys: PUT-YOUR-LICENSE-HERE
```

### Fields - System

- **useVirtualThreads**<br />
  This option controls whether YueMi-Spigot uses Java Virtual Threads (Project Loom) for its async scheduler, or falls back to the traditional Paper thread pool.
  > default: `true`

- **licenseKeys**<br />
  Placeholder for licensing or authentication key.
  > default: `PUT-YOUR-LICENSE-HERE`