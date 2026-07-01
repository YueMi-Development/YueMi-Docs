# RandomLocationsNearCaster / RandomLocationsNearOrigin Targeter

Targets random location coordinates in a radius around the caster or origin.

## Shorthands & Aliases

- `randomlocationsnearcaster`
- `randomlocations`
- `rlnc`
- `randomlocationsnearorigin`
- `rlo`
- `randomlocationsorigin`
- `rlno`

## Options

- `radius / r`: Maximum offset radius (default: 5.0).
- `amount / a`: Number of random locations to pick (default: 3).

## Example Configuration

```json5
targeter: "randomlocations{r=8,a=5}"
```