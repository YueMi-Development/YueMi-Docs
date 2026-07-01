# Delay Mechanic

Pauses the execution of subsequent mechanics in the skill pipeline for a set duration of Minecraft game ticks or seconds.

## Options

- `ticks`: The duration of the delay in game ticks (20 ticks = 1 second).
- `seconds`: The duration of the delay in seconds.

## Example Configuration

```json5
mechanics: [
  "delay{ticks=40}",   // Delay by 40 ticks (2 seconds)
  "delay{seconds=3}"   // Delay by 3 seconds
]
```
