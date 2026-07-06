---
sidebar_position: 2
title: Skill Definitions
---

# Skill Definitions

Custom skills are defined inside JSON5 files in the `skills/` directory.

## Configuration Structure

Each skill JSON5 file supports the following properties:
* `name`: The display name of the skill.
* `mechanics`: A list of mechanic objects that execute sequentially.
  * `mechanic`: The name and parameters of the mechanic (e.g., `damage{amount=5}`).
  * `targeter`: The targets selection rules (e.g., `livingincone{r=5;a=45}`).
  * `conditions`: Optional conditions that filter whether this mechanic executes.

### Example Configuration (`fire_breath.json5`)

```json5
{
  // Skill that ignites and damages all entities in a cone in front of the caster
  name: "Fire Breath",
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
