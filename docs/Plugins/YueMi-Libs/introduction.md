---
sidebar_position: 1
title: Introduction
---

# Introduction

**YueMi Libs** is a robust, lightweight, and extensible library plugin designed for Minecraft servers running **PaperMC (1.21+ / Java 21)**. It simplifies plugin development by providing uniform, performance-optimized, and clean abstraction layers for common tasks, such as handling economies and managing custom/vanilla items.

Rather than implementing third-party hooks (like Vault or CraftEngine) repeatedly in every plugin, you can rely on YueMi Libs as a single dependency that orchestrates these integrations transparently.

---

## Key Capabilities

*   **Unified Economy Access**: A simple, provider-independent Economy API that hooks into standard backends (e.g. Vault) automatically.
*   **Multi-Namespace Items API**: Retrieve, give, take, or query items concurrently across different namespace providers (e.g. vanilla `minecraft` and `craftengine`).
*   **Item Match Modes**: Match vanilla items strictly using NBT data (`NBT`), Custom Model Data (`CUSTOM_MODEL_DATA`), or simple Material IDs (`ID`).
*   **Dynamic Configurations**: Automatically manages configuration upgrades step-by-step using an built-in migrator.

---

## Modules

The project uses a two-tier module architecture:
1.  **core-api**: Contains public interfaces, constants, and static helpers. It has zero server-side code or logic, making it ideal as a `compileOnly` dependency for your projects.
2.  **core-plugin**: The actual deployable plugin JAR containing the backend listeners, hooks, config management, and implementations. It shades `core-api` internally.
