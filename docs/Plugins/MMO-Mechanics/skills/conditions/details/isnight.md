# IsNight Condition

Evaluates to `true` if the caster's world time is currently during nighttime hours.

## Details

Nighttime hours are defined as being between tick `12000` and `23000` of the daylight cycle.

## Example Configuration

```json5
conditions: [
  "isnight"
]
```
