---
sidebar_position: 2
title: EconomyApi
---

# EconomyApi

> Part of **YueMi-MC-Libs** · Economy Module

Main entry point for the economy system.

## EconomyApi

```java
public interface EconomyApi {
    @Nullable EconomyProvider getActiveProvider();
    void registerProvider(@NotNull EconomyProvider provider);
    boolean setActiveProvider(@NotNull String name);
    @NotNull Collection<EconomyProvider> getProviders();

    // Convenience methods delegating to active provider
    double getBalance(@NotNull OfflinePlayer player);
    boolean withdraw(@NotNull OfflinePlayer player, double amount);
    boolean deposit(@NotNull OfflinePlayer player, double amount);
    boolean setBalance(@NotNull OfflinePlayer player, double amount);
}
```

## EconomyProvider

Implement this interface to add support for a custom economy backend.

```java
public interface EconomyProvider {
    @NotNull String getName();                          // unique provider name
    boolean isAvailable();                              // false if backend not found

    double getBalance(@NotNull OfflinePlayer player);
    boolean withdraw(@NotNull OfflinePlayer player, double amount);
    boolean deposit(@NotNull OfflinePlayer player, double amount);
    boolean setBalance(@NotNull OfflinePlayer player, double amount);
}
```

## VaultEconomyProvider

Built-in provider that integrates with any Vault-compatible economy plugin.

```java
// Automatically registered if Vault is present
// Uses Vault's Economy API as the backend
```

## Registering a Custom Provider

```java
public class MyEconomyProvider implements EconomyProvider {
    @Override
    public @NotNull String getName() { return "myeconomy"; }

    @Override
    public boolean isAvailable() { return true; }

    @Override
    public double getBalance(@NotNull OfflinePlayer player) {
        return myDatabase.getBalance(player.getUniqueId());
    }

    @Override
    public boolean withdraw(@NotNull OfflinePlayer player, double amount) {
        return myDatabase.withdraw(player.getUniqueId(), amount);
    }

    @Override
    public boolean deposit(@NotNull OfflinePlayer player, double amount) {
        return myDatabase.deposit(player.getUniqueId(), amount);
    }

    @Override
    public boolean setBalance(@NotNull OfflinePlayer player, double amount) {
        return myDatabase.setBalance(player.getUniqueId(), amount);
    }
}

// Register:
economy.registerProvider(new MyEconomyProvider());
economy.setActiveProvider("myeconomy");
```
