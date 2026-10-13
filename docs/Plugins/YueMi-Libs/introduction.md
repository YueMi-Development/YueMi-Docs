---
sidebar_position: 1
title: Introduction
---

# Introduction

**YueMi Libs** is a robust, lightweight, and extensible library plugin designed for Minecraft servers running **PaperMC (1.21+ / Java 21)**. It provides uniform, performance-optimised abstraction layers for common tasks — economy, custom items, GUI building, and event subscription — so that game plugins don't need to re-implement these layers on their own.

Rather than writing third-party hooks (like Vault or CraftEngine) repeatedly in every plugin, you can rely on YueMi Libs as a single dependency that orchestrates these integrations transparently.

---

## Key Capabilities

- **Unified Economy Access** — a provider-independent `EconomyApi` that hooks into standard backends (e.g. Vault) automatically.
- **Multi-Namespace Items API** — retrieve, give, take, or query items across different providers (`minecraft:`, `craftengine:`, `itemsadder:`, `nexo:`) under a single interface.
- **Item Match Modes** — match vanilla items strictly via NBT, `CUSTOM_MODEL_DATA`, or simple `ID`.
- **Dynamic Configurations** — built-in migrator (`MC-Config-Libs`).
- **GUI Building API** — `GuiApi` with a `Builder` + layered `GuiLayer` / `GuiItem` model, plus per-slot `SlotBehavior` controls (place / pickup / drag / shift).
- **Event Subscription API** — `EventApi` with typed `EventProvider` namespaces and a `bukkit().subscribe(...).priority(...).handler(...)` chain, so consumers don't call `getPluginManager().registerEvents(...)` directly.

---

## Modules

The project uses a two-tier module architecture:

1. **core-api** — public interfaces, constants, and static helpers. Zero server-side code; ideal as a `compileOnly` dependency.
2. **core-plugin** — the actual deployable JAR (shades `core-api` internally) and ships the runtime implementations.

The public surface is published as a **single Maven artifact**: `org.yuemi:YueMiLibs-api:<version>`. Internally that artifact bundles the per-feature packages (`gui`, `event`, `items`, `economy`), but you only need to depend on the one artifact.

```kotlin
dependencies {
    implementation("org.yuemi:YueMiLibs-api:2.3.12")
}
```

The implementation modules are an internal split — they exist so the runtime can lazy-load subsystems and so test code can pull individual modules. End-user plugins only need the umbrella `YueMiLibs-api` dependency.
