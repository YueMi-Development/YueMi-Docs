# EntitiesInRadius Targeter

Targets all living entities within a specified radius around the caster.

## Shorthands & Aliases

- `entitiesinradius`
- `livingentitiesinradius`
- `livinginradius`
- `allinradius`
- `eir`
- `entitiesnearorigin`
- `eno`

## Options

- `r / radius`: The radius to search within (default: 5.0).

## Example Configuration

```json5
targeter: "entitiesinradius{radius=10}"
```