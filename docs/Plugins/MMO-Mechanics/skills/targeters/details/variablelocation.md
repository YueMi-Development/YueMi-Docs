# VariableLocation Targeter

Targets the location stored in a specified skill variable.

## Shorthands & Aliases

- `variablelocation`
- `varlocation`

## Options

- `var / variable / v`: The name of the variable to read the location from.

## Example Configuration

```json5
targeter: "variablelocation{var=my_saved_point}"
```