---
title: Mechanics
sidebar_position: 1
---

# Skill Mechanics

Mechanics execute actions on the targets resolved by targeters. Click on any mechanic name to see options and details.

---

## Supported Mechanics

| Mechanic | Aliases / Shorthands | Description |
| :--- | :--- | :--- |
| **[Delay](./details/delay.md)** | `delay` | A Mechanic representing a execution pause in ticks or seconds. |
| **[Skill](./details/skill.md)** | `skill`, `cast`, `metaskill` | Casts another skill by name on the target. |
| **[Lightning](./details/thunder.md)** | `lightning` | Strikes a bolt of lightning at targeted locations. |
| **[Message](./details/message.md)** | `message`, `msg`, `jsonmessage` | Sends raw JSON component messages to targeted players. |
| **[Sendtitle](./details/sendtitle.md)** | `sendtitle`, `title` | Displays title and subtitle text overlays on player screens. |
| **[Sendactionmessage](./details/sendactionmessage.md)** | `sendactionmessage`, `actionbar` | Displays action bar text above the hotbar. |
| **[Feed](./details/feed.md)** | `feed` | Feeds targeted players, increasing food and saturation levels. |
| **[Closeinventory](./details/closeinventory.md)** | `closeinventory` | Closes open container screen GUIs. |
| **[Setgamemode](./details/setgamemode.md)** | `setgamemode`, `gamemode` | Sets player game modes (Survival, Creative, Adventure, Spectator). |
| **[Damage](./details/damage.md)** | `damage`, `basedamage`, `percentdamage` | Deals damage to targeted entities as raw values, multiplier of caster base damage, or percentage of target health. |
| **[Heal](./details/heal.md)** | `heal`, `healpercent` | Restores health to target entities by raw values or max health percentages. |
| **[Potion](./details/potion.md)** | `potion`, `potionclear` | Applies potion effects with custom amplifier/duration, or clears active potion effects. |
| **[Velocity](./details/velocity.md)** | `velocity`, `directionalvelocity`, `throw`, `propel` | Adjusts entity speed and velocity vectors, including relative pushes/throws. |
| **[Ignite](./details/ignite.md)** | `ignite`, `extinguish` | Sets targeted entities on fire for a specified duration, or extinguishes active fire. |
| **[Addtrade](./details/addtrade.md)** | `addtrade` | Appends custom recipes/trades to villagers. |
| **[Animatearmorstand](./details/animatearmorstand.md)** | `animatearmorstand` | Animates armor stands by rotating their limbs over a duration of ticks. |
| **[Posearmorstand](./details/posearmorstand.md)** | `posearmorstand` | Sets specific rotations (head, body, arms, legs) on targeted armor stands. |
| **[Armanimation](./details/armanimation.md)** | `armanimation`, `swingoffhand` | Triggers targeted entities to swing their main hand or off hand. |
| **[Barcreate](./details/barcreate.md)** | `barcreate`, `barremove`, `barset` | Shows, removes, or modifies progress bars on top of player screens. |
| **[Equip](./details/equip.md)** | `equip`, `equipcopy` | Forces targeted entities to equip items or copies equipment configurations. |
| **[Setname](./details/setname.md)** | `setname` | Sets a custom name visible above targeted entities with full text coloring and placeholders. |
| **[Togglesitting](./details/togglesitting.md)** | `togglesitting`, `wolfsit` | Toggles or forces sitting states for sittable pets like dogs, cats, foxes, and parrots. |
| **[Setmobcolor](./details/setmobcolor.md)** | `setmobcolor` | Changes dye/collar colors for sheep, wolves, cats, llamas, and shulkers. |
| **[Breakblock](./details/breakblock.md)** | `breakblock`, `breakblockandgiveitem` | Breaks the block at the target location, with options to drop items naturally or give them to the player. |
| **[Setblocktype](./details/setblocktype.md)** | `setblocktype` | Changes the type/material of blocks at target locations with optional physics updates. |
| **[Setblockopen](./details/setblockopen.md)** | `setblockopen` | Opens or closes doors, trapdoors, fence gates, chests, or shulker boxes at target locations. |
| **[Togglelever](./details/togglelever.md)** | `togglelever`, `pushbutton` | Toggles levers, or triggers buttons to power on and automatically shut off after a delay. |
| **[Pushblock](./details/pushblock.md)** | `pushblock` | Physically slides blocks in a chosen direction (cardinal or facing direction). |
| **[Blockdestabilize](./details/blockdestabilize.md)** | `blockdestabilize` | Destabilizes blocks, causing them to fall downwards under gravity as active falling block entities. |
| **[Blockmask](./details/blockmask.md)** | `blockmask`, `blockunmask` | Temporarily masks or unmasks blocks client-side, showing fake block materials to players. |
| **[Blockphysics](./details/blockphysics.md)** | `blockphysics` | Triggers physical block updates at targeted locations. |
| **[Fillchest](./details/fillchest.md)** | `fillchest` | Fills targeted containers (chests, barrels, shulker boxes) with items, optionally clearing them first. |
| **[Spring](./details/spring.md)** | `spring` | Spawns temporary liquid sources (water or lava) that vanish after a duration. |
| **[Sound](./details/sound.md)** | `sound`, `stopsound` | Plays sound effects at locations or stops sounds for targeted players. |
| **[Explosion](./details/explosion.md)** | `explosion`, `fakeexplosion` | Spawns block-breaking explosions or client-side cosmetic visual explosions. |
| **[Weather](./details/weather.md)** | `weather` | Modifies world weather (Clear, Rain, Storm) and duration. |
| **[Time](./details/time.md)** | `time` | Sets absolute or relative world times. |
| **[Command](./details/command.md)** | `command`, `cmd` | Executes console commands or target-performed player commands. |
| **[Particle](./details/particle.md)** | `particle`, `particlebox`, `particlering` | Spawns visual shapes (point particles, circles, ring outlines, box borders) around targets. |
