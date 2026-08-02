---
sidebar_position: 1
title: Introduction
---

# MC Config Libs

**MC Config Libs** is a reusable configuration migration library for [PaperMC](https://papermc.io/) plugins. Drop it in as a dependency and get automatic, versioned `config.yml` migrations, no boilerplate required.

---

## Features

*   **Auto-discovery**: scans a package at startup and loads every `MigrationStep` implementation automatically, whether running from a directory (IDE) or a shaded JAR on a server.
*   **Sequential migration**: steps are sorted by `getTargetVersion()` and applied in order, skipping versions already applied.
*   **Saves only when needed**: `config.yml` is written to disk only if at least one step was applied.
*   **Zero naming conventions**: migration classes can be named anything; the target version comes from `getTargetVersion()`.
*   **Paper API native**: built against Paper API 1.21.6, fully compatible with modern Minecraft.

