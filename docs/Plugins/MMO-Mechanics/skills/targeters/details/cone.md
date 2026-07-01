# Cone Targeter

Generates a list of locations forming a cone shape on the ground in front of the caster.

## Shorthands & Aliases

- `cone`

## Options

- `angle`: Angle size of the cone sector in degrees (default: 45.0).
- `length`: Max length from origin (default: 10.0).
- `points`: Number of locations to generate inside the cone sector (default: 10).

## Example Configuration

```json5
targeter: "cone{angle=60,length=12,points=15}"
```