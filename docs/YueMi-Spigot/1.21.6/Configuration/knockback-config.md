---
sidebar_position: 1
---
# Knockbacks
Customize Minecraft Knockback Mechanism.

## Config Preview
```yaml
knockback:
  friction: 2.0
  horizontal: 0.6
  vertical: 0.35
  verticalLimit: 0.4
  extraHorizontal: 0.425
  extraVertical: 0.085
```

### Fields - Knockback

- **friction**<br />
  Global friction applied post-knockback.
  > default: `2.0`

- **horizontal**<br />
  Base horizontal knockback multiplier.
  > default: `0.6`

- **vertical**<br />
  Base vertical knockback multiplier.
  > default: `0.35`

- **verticalLimit**<br />
  Maximum vertical velocity after knockback.
  > default: `0.4`

- **extraHorizontal**<br />
  Additional horizontal knockback during sprinting.
  > default: `0.425`

- **extraVertical**<br />
  Additional vertical knockback during sprinting.
  > default: `0.085`