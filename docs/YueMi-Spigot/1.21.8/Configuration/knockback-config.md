---
sidebar_position: 1
---
# Knockbacks
Customize Minecraft Knockback Mechanism.

By default, the `global` configuration is used for all knockback events. You can override the global settings for specific triggers/cause types by setting `enabled: true` in their respective configuration sections.

## Config Preview
```yaml
global:
  friction: 2.0
  horizontal: 0.6
  vertical: 0.35
  verticalLimit: 0.4
  extraHorizontal: 0.425
  extraVertical: 0.085
damage:
  enabled: false
  friction: 2.0
  horizontal: 0.6
  vertical: 0.35
  verticalLimit: 0.4
  extraHorizontal: 0.425
  extraVertical: 0.085
entity_attack:
  enabled: false
  friction: 2.0
  horizontal: 0.6
  vertical: 0.35
  verticalLimit: 0.4
  extraHorizontal: 0.425
  extraVertical: 0.085
explosion:
  enabled: false
  friction: 2.0
  horizontal: 0.6
  vertical: 0.35
  verticalLimit: 0.4
  extraHorizontal: 0.425
  extraVertical: 0.085
shield_block:
  enabled: false
  friction: 2.0
  horizontal: 0.6
  vertical: 0.35
  verticalLimit: 0.4
  extraHorizontal: 0.425
  extraVertical: 0.085
sweep_attack:
  enabled: false
  friction: 2.0
  horizontal: 0.6
  vertical: 0.35
  verticalLimit: 0.4
  extraHorizontal: 0.425
  extraVertical: 0.085
push:
  enabled: false
  friction: 2.0
  horizontal: 0.6
  vertical: 0.35
  verticalLimit: 0.4
  extraHorizontal: 0.425
  extraVertical: 0.085
unknown:
  enabled: false
  friction: 2.0
  horizontal: 0.6
  vertical: 0.35
  verticalLimit: 0.4
  extraHorizontal: 0.425
  extraVertical: 0.085
air:
  enabled: false
  friction: 2.0
  horizontal: 0.6
  vertical: 0.35
  verticalLimit: 0.4
  extraHorizontal: 0.425
  extraVertical: 0.085
```

### Fields per Cause Type
Configure knockback values per cause type. **global** is the fallback for disabled types.

Each type (e.g., `global`, `damage`, `entity_attack`, `explosion`, `shield_block`, `sweep_attack`, `push`, `unknown`, `air`) supports the following settings (with `global` omitting `enabled`):

- **enabled**<br />
  Whether custom configurations are enabled for this specific cause type. If `false`, the values from `global` are used instead.
  > default: `false`

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