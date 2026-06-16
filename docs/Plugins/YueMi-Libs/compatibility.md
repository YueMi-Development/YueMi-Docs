---
sidebar_position: 4
title: Compatibility
---

# Compatibility

YueMi Libs is designed to connect various server subsystems into a unified interface. Below is the list of compatible plugins and hook types supported by YueMi Libs.

---

## Economy Plugins

YueMi Libs integrates with any economy system that exposes itself through the standard **Vault** API.

| Plugin | Hook Type | Status | Notes |
| :--- | :--- | :--- | :--- |
| **Vault** | Core API Bridge | **Compatible** | Required to bridge standard economy plugins. |
| **EssentialsX** | Vault | **Compatible** | Supported automatically via Vault. |
| **CMI** | Vault | **Compatible** | Supported automatically via Vault. |
| **PlayerPoints** | Vault / Custom | **Compatible** | Supported automatically via Vault. |

---

## Item Providers

The items provider API supports multiple namespaces concurrently. You can reference items from different plugins using their namespace prefixes.

| Plugin / Registry | Namespace Prefix | Status | Notes |
| :--- | :--- | :--- | :--- |
| **Vanilla Minecraft** | `minecraft:` | **Compatible** | Built-in. Supports materials and CustomModelData bracket syntax. |
| **CraftEngine** | `craftengine:` | **Compatible** | Supported out-of-the-box (requires CraftEngine 26.6.2+). |
| **ItemsAdder** | `itemsadder:` | *Planned* | Future integration. |
| **Nexo** | `nexo:` | *Planned* | Future integration. |

---

## Other Integrations

*   **ProtocolLib**: Used as a soft dependency for advanced packet handling or custom model parsing optimizations where needed.
