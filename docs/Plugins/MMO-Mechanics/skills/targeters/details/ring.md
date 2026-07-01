# Ring / RingAroundOrigin Targeter

Generates points forming a ring of target locations around the caster/origin.

## Shorthands & Aliases

- `ring`
- `ringaroundorigin`
- `ringorigin`
- `rao`

## Options

- `radius / r`: Radius of the ring (default: 5.0).
- `points / p`: Total number of locations to distribute evenly along the ring boundary (default: 12).

## Example Configuration

```json5
targeter: "ring{r=6,p=16}"
```