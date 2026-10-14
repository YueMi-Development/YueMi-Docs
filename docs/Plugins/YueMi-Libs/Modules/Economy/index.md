---
sidebar_position: 1
title: Economy Module
---

# Economy Module

> Part of **YueMi-MC-Libs**

Multi-provider economy system with built-in Vault integration.

## APIs

| API | Description |
|-----|-------------|
| [EconomyApi](./EconomyApi) | Main economy API with provider management |

## Quick Start

```java
EconomyApi economy = api.getEconomy();

// Get balance
double balance = economy.getBalance(player);

// Deposit and withdraw
economy.deposit(player, 100.0);
economy.withdraw(player, 50.0);

// Provider management
economy.setActiveProvider("vault");
```

## Built-in Providers

| Provider | Description |
|----------|-------------|
| **VaultEconomyProvider** | Integrates with any Vault-compatible economy plugin |
