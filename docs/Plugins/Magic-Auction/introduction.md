---
title: Introduction
sidebar_position: 1
---

# Magic Auction

**Magic Auction** is a PaperMC plugin that implements an engaging, container-bidding auction minigame. Inspired by TV storage auctions, 4 players compete across escalating rounds to bid on mystery containers containing hidden items.

---

## Core Game Cycle

Each auction session proceeds through distinct phases:

1. **Auction Starts** (exactly 4 players).
2. **Preview Phase**: Item masking and glass properties are shown in the GUI, with a live countdown timer.
3. **Bidding Phase**: Players submit bids via an Anvil GUI.
4. **Bidding Graph**: Standings and bids are displayed in a color-coded live progress graph.
5. **Round Evaluation**:
   * **Highest Bid >= BIN Threshold**: The highest bidder wins immediately -> **Winner Reveal Phase** (5s delay + item reveal) -> **Auction Ends**.
   * **Highest Bid < BIN Threshold**:
     * If rounds remain -> Proceed to the **next round** with a lower overbid multiplier.
     * If all rounds are completed -> **Auction Ends** with no winner.

### 1. Preview Phase
* Players are shown a chest interface with container items.
* Items are initially hidden/masked behind colored glass panes based on their properties (rarity, size, type).
* A live action bar countdown (color-coded green, yellow, red) shows the remaining preview time.

### 2. Bidding Phase
* Players enter their bids through an Anvil GUI.
* The GUI displays their current balance and the current round's overbid multiplier.
* Players have a set amount of time to bid; if they timeout, their bid defaults to `$1`.

### 3. Bidding Graph Phase
* Once all bids are submitted, a animated bar graph displays the standings.
* Standings are color-coded:
  * **Green**: Winning bid (meets the BIN threshold).
  * **Yellow**: Highest bid that failed BIN, or second-highest (blocking) bid.
  * **Red**: All other bids.
* Displays a live multiplier indicator and player heads.

### 4. Round Evaluation (The BIN Mechanic)

To win the auction instantly (**BIN - Buy It Now**), the highest bidder's bid must satisfy the BIN threshold:
`Bid >= Second Highest Bid * Round Multiplier`
*(If only one player bids, the arena's `base-price` serves as the second-highest bid floor.)*

Each round features an overbid multiplier that decreases over time (making it easier to win in later rounds, but with less mystery).

### 5. Winner Reveal Phase
* When a player wins, the reveal GUI opens.
* The items remain masked for a **5-second suspense delay** before being revealed one-by-one to their true identities.
* Virtual item worth is credited to the winner's economy balance. Physical items trigger custom commands or drop clean items into the winner's inventory.

---

## Features & Mechanics

* **Deterministic Seed System**: Optional seed input ensures reproducible item layouts and shuffled event configurations.
* **Round Events**: Random reveals (revealing item types, sizes, or rarities) that occur before rounds start to influence bidding decisions.
* **Simulated Bot Players**: Fill empty matchmaking slots or test the game using simulated bots with human-like bidding delays.
* **Robust Economy Integration**: Native support for Vault and PlayerPoints via YueMi Libs.
