---
sidebar_position: 2
---
# System Commands
List and Usage of System Commands.

## Themes Command
Set the theme colors and display name for the server's UI. All subcommands require the same permission.

| Command | Description | Permissions |
|---------|-------------|-------------|
| `/themes setmain <color>` | Set the main color of the theme | `yuemi.system.theme` |
| `/themes setsecondary <color>` | Set the secondary color of the theme | `yuemi.system.theme` |
| `/themes settitle <color>` | Set the title color of the theme | `yuemi.system.theme` |
| `/themes setspigotname <name>` | Set the Spigot server name displayed in the UI | `yuemi.system.theme` |

## Knockback Command
Configure the server's knockback behavior by adjusting friction, horizontal, vertical, vertical limits, and extra components. All subcommands require the same permission.

| Command | Description | Permissions |
|---------|-------------|-------------|
| `/knockback setfriction <value>` | Set friction used in knockback calculations | `yuemi.system.knockback` |
| `/knockback sethorizontal <value>` | Set horizontal knockback multiplier | `yuemi.system.knockback` |
| `/knockback setvertical <value>` | Set vertical knockback multiplier | `yuemi.system.knockback` |
| `/knockback setverticallimit <value>` | Set vertical maximum knockback limit | `yuemi.system.knockback` |
| `/knockback setextrahorizontal <value>` | Set extra horizontal knockback component | `yuemi.system.knockback` |
| `/knockback setextravertical <value>` | Set extra vertical knockback component | `yuemi.system.knockback` |
