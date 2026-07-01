# RandomRingPoint Targeter

Targets a random point location along a ring around the caster.

## Shorthands & Aliases

- `randomringpoint`

## Options

- `radius / r`: Radius of the ring (default: 5.0).
- `amount / a`: Number of random points to pick (default: 1).

## Example Configuration

```json5
targeter: "randomringpoint{r=5,a=3}"
```