# EntitiesInRing Targeter

Targets all living entities within a ring (between a minimum and maximum radius) around the caster.

## Shorthands & Aliases

- `entitiesinring`
- `eirr`
- `entitiesinringnearorigin`
- `erno`

## Options

- `min / minr / minradius`: Inner boundary radius of the ring (default: 2.0).
- `max / maxr / maxradius`: Outer boundary radius of the ring (default: 5.0).

## Example Configuration

```json5
targeter: "entitiesinring{min=3,max=8}"
```