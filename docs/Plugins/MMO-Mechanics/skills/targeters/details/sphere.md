# Sphere Targeter

Generates point locations forming a sphere shell around the caster.

## Shorthands & Aliases

- `sphere`

## Options

- `radius / r`: Radius of the sphere shell (default: 3.0).
- `points / p`: Total number of locations distributed evenly on the shell (default: 20).

## Example Configuration

```json5
targeter: "sphere{radius=4,points=30}"
```