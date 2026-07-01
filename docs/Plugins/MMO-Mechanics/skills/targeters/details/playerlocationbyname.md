# PlayerLocationByName Targeter

Targets the current location of a specific player by their name.

## Shorthands & Aliases

- `playerlocationbyname`

## Options

- `name`: The player name expression (supports placeholders).

## Example Configuration

```json5
targeter: "playerlocationbyname{name=%player_name%}"
```