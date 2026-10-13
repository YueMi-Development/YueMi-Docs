---
sidebar_position: 2
title: Skill Definitions
---

# Skill Definitions

Custom skills are defined inside JSON5 files in the `skills/` directory.

## Configuration Structure

Each skill JSON5 file supports the following properties:
* `name`: The display name of the skill.
* `triggers`: A list of trigger ids that decide when the skill fires. The standard ids are:
  * `onAttack` — caster attacks an entity
  * `onDamaged` — caster takes damage
  * `onDeath` / `onKill` / `onPlayerKill` — lifecycle
  * `onTimer` — periodic
  * `onClick` — player interact
  * `onEquip` / `onUnequip` — item equipped in (or removed from) an accessory slot, or a vanilla armor slot (see `EquipTriggerRegistration`)
  * `command` — direct cast via `MmoMechanicsApi.castSkill`
* `mechanics`: A list of mechanic objects that execute sequentially.
  * `mechanic`: The name and parameters of the mechanic (e.g., `damage{amount=5}`).
  * `targeter`: The targets selection rules (e.g., `livingincone{r=5;a=45}`).
  * `conditions`: Optional conditions that filter whether this mechanic executes.

Triggers can be declared as either a list of strings or a list of `{trigger: "...", id: "..."}` objects.

### Example Configuration (`fire_breath.json5`)

```json5
{
  // Skill that ignites and damages all entities in a cone in front of the caster
  name: "Fire Breath",
  triggers: ["onAttack"],
  mechanics: [
    {
      mechanic: "ignite{ticks=60}",
      targeter: "livingincone{r=8;a=45}",
      conditions: []
    },
    {
      mechanic: "damage{amount=6}",
      targeter: "livingincone{r=8;a=45}",
      conditions: []
    }
  ]
}
```

### Equip-trigger Example (`flame_aura.json5`)

When a player equips an item (in an accessory slot or as armor) whose `trigger` list includes `onEquip`, the matching skills are run with the player as caster.

```json5
{
  // Skill: when the wearer is hit, ignite and damage the attacker
  name: "Flame Aura",
  triggers: ["onDamaged", "onEquip"],
  mechanics: [
    {
      mechanic: "ignite{ticks=60}",
      targeter: "trigger",
      conditions: []
    },
    {
      mechanic: "damage{amount=2}",
      targeter: "trigger",
      conditions: []
    }
  ]
}
```
