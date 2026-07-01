# LivingInCone / EntitiesInCone Targeter

Targets living entities located inside a cone sector in front of the caster.

## Shorthands & Aliases

- `livingincone`
- `entitiesincone`
- `livingentitiesincone`
- `leic`
- `eic`

## Options

- `angle`: The angle size of the cone in degrees (default: 45.0).
- `length / len / l`: The max distance of the cone projection (default: 10.0).
- `rotation / rot / r`: Horizontal offset angle in degrees relative to the facing direction (default: 0.0).

## Example Configuration

```json5
targeter: "livingincone{angle=90,length=15,rotation=0}"
```