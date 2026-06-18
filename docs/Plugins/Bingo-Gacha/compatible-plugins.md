# Compatible Plugins

Bingo Gacha works seamlessly with other plugins to enrich card challenges, economies, and rewards. Integration is handled either directly or through **YueMi Libs**.

---

## Economy Plugins

You can configure economies for purchase costs, roll costs, and card rewards.

*   **Vault** (Direct / YueMi Libs)
    *   *Usage*: Used directly for standard currency rewards or charging balances.
    *   *Details*: Supported natively out-of-the-box and automatically routed through YueMi Libs if installed.
*   **PlayerPoints** (via YueMi Libs)
    *   *Usage*: Charge players premium points or distribute them as rewards upon completing cards.
    *   *Details*: Handled automatically when PlayerPoints is set as the active provider in YueMi Libs.

---

## Custom Item Plugins

Make cards require custom items or reward players with items from other plugins when they complete a line or the card.

*   **CraftEngine** (via YueMi Libs / Direct)
    *   *Format*: `CraftEngine` namespace keys (e.g. `craftengine:pack:item_id` or legacy hook).
    *   *Details*: Resolves items defined in CraftEngine items configs, supporting sub-namespaces.
*   **Nexo** (via YueMi Libs / Direct)
    *   *Format*: `Nexo` namespace keys (e.g. `nexo:pack:item_id`).
    *   *Details*: Supports custom items, blocks, and furniture packs from Nexo.
*   **ItemsAdder** (via YueMi Libs / Direct)
    *   *Format*: `ItemsAdder` namespace keys (e.g. `itemsadder:pack:item_id`).
    *   *Details*: Supports all custom items, custom blocks, and custom assets.

---

## Placeholders & Display

*   **PlaceholderAPI** (Direct)
    *   *Details*: Displays Bingo Gacha stats in your scoreboard, tab lists, chat, or holograms using Placeholders. See the plugin commands and configs for full details.
