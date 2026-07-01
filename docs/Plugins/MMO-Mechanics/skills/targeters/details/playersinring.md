# PlayersInRing Targeter

Targets players located within a ring (between a minimum and maximum radius).

## Shorthands & Aliases

- `playersinring`

## Options

- `min / minr / minradius`: Inner boundary radius (default: 2.0).
- `max / maxr / maxradius`: Outer boundary radius (default: 5.0).

## Example Configuration

```json5
targeter: "playersinring{min=5,max=10}"
```