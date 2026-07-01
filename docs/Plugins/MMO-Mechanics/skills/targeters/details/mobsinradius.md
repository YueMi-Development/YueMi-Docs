# MobsInRadius Targeter

Targets monsters or vanilla mobs of specified types within a radius.

## Shorthands & Aliases

- `mobsinradius`
- `mir`
- `mobsnearorigin`

## Options

- `r / radius`: The radius around the origin (default: 5.0).
- `types / type / t`: Comma-separated list of EntityType names to filter by.

## Example Configuration

```json5
targeter: "mobsinradius{r=12,types=ZOMBIE,SKELETON}"
```