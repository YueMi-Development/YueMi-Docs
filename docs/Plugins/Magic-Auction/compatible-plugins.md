---
title: Compatible Plugins
sidebar_position: 98
---

# Compatible Plugins

Magic Auction integrates with various third-party plugins to support robust economies and custom item systems, primarily routed through **YueMi Libs**.

---

## Economy Plugins

Economy integration is crucial for bidding balances and rewarding winners of virtual items.

*   **Vault** (Direct / YueMi Libs)
    *   *Usage*: Used for player balances, bid verification, and virtual item payouts.
    *   *Details*: Supported natively and automatically routed through YueMi Libs.
*   **PlayerPoints** (via YueMi Libs)
    *   *Usage*: Bid using points or reward players with premium points.
    *   *Details*: Activated automatically when PlayerPoints is configured as the active provider in YueMi Libs.

---

## Custom Item Plugins

You can configure custom items from other plugins to serve as base items in the auction grid or as physical rewards for winning.

*   **CraftEngine** (via YueMi Libs / Direct)
    *   *Format*: `craftengine:pack:item_id`
    *   *Details*: Resolves items defined in CraftEngine items configs, supporting sub-namespaces.
*   **Nexo** (via YueMi Libs / Direct)
    *   *Format*: `nexo:pack:item_id`
    *   *Details*: Supports custom items, blocks, and furniture packs from Nexo.
*   **ItemsAdder** (via YueMi Libs / Direct)
    *   *Format*: `itemsadder:pack:item_id`
    *   *Details*: Supports custom items, custom blocks, and assets.

---

## Placeholders & Display

*   **PlaceholderAPI** (Direct)
    *   *Details*: Display player auction wins, current bid statuses, or matchmaking queue status.
