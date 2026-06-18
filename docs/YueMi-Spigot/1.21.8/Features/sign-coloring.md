---
sidebar_position: 3
---
# Sign Coloring System

This page explains the **sign coloring and formatting system** in YueMi-Spigot, and how permissions control access to different styles.

## Overview

Players can customize the text on signs using the `&` character followed by a color or formatting code.  
YueMi-Spigot translates these into Minecraft’s native section sign codes (`§`).

Example:
```
&cHello &lWorld
```
becomes:  
**Hello** (in red) and **World** (in bold).

## Permission Nodes

| Permission                 | Description |
|-----------------------------|-------------|
| <code style={{whiteSpace: 'nowrap'}}>yuemi.sign.color</code> | Allows use of `&0`–`&f` color codes (black → white, plus standard colors). |
| <code style={{whiteSpace: 'nowrap'}}>yuemi.sign.style</code> | Allows use of `&l`, `&o`, `&m`, `&n` formatting codes (bold, italic, strikethrough, underline). |
| <code style={{whiteSpace: 'nowrap'}}>yuemi.sign.magic</code> | Allows use of `&k` "magic" obfuscated text effect. |

## Examples

| Input Text | Permission Required | Result |
|------------|----------------------|--------|
| `&aWelcome` | `yuemi.sign.color` | <span style={{color: 'green'}}>Welcome</span> |
| `&lBold Text` | `yuemi.sign.style` | **Bold Text** |
| `&kSecret` | `yuemi.sign.magic` | <span style={{color: 'gray'}}>▒▒▒▒▒▒</span> (random obfuscated characters) |
