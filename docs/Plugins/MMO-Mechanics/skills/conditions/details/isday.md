# IsDay Condition

Evaluates to `true` if the caster's world time is currently during daytime hours.

## Details

Daytime hours are defined as being between tick `0` and `12000` (and `23000` to `24000` of the daylight cycle).

## Example Configuration

```json5
conditions: [
  "isday"
]
```
