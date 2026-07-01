# Uuid / UniqueIdentifier Targeter

Targets a specific entity by its unique UUID.

## Shorthands & Aliases

- `uuid`
- `uniqueidentifier`

## Options

- `uuid`: The UUID string of the target entity (supports placeholders).

## Example Configuration

```json5
targeter: "uuid{uuid=%some_entity_uuid%}"
```