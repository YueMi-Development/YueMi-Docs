# ForwardWall Targeter

Generates a wall-like plane grid of locations in front of the caster.

## Shorthands & Aliases

- `forwardwall`

## Options

- `width / w`: Width of the grid plane (default: 3.0).
- `height / h`: Height of the grid plane (default: 3.0).
- `distance / d`: Distance forward to position the center of the wall (default: 5.0).

## Example Configuration

```json5
targeter: "forwardwall{w=5,h=4,d=6}"
```