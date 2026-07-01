# TargetPredictedLocation Targeter

Targets the predicted location of the target based on its current movement direction and speed.

## Shorthands & Aliases

- `targetpredictedlocation`
- `targetpredictedloc`
- `tpl`
- `predictedtargetlocation`

## Options

- `t / ticks`: Ticks in the future to project the target location (default: 5.0).

## Example Configuration

```json5
targeter: "targetpredictedlocation{ticks=10}"
```