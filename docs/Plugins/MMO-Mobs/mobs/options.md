---
sidebar_position: 1
title: Mob Options
---

# Mob Options

Custom mobs in MMO Mobs support a comprehensive `options` configuration block. This allows you to fine-tune the attributes, behaviors, immunities, and visual traits of both universal and type-specific mobs.

```json5
{
  name: "<red>Elite Guardian",
  type: "ZOMBIE",
  health: 150,
  options: {
    AlwaysShowName: true,
    MovementSpeed: 0.28,
    Scale: 1.5,
    PreventSunburn: true,
    Collidable: false
  }
}
```

---

## Universal Options

These options can be applied to all custom mobs (mostly affecting `LivingEntity`).

| Option | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `AlwaysShowName` | Boolean | `false` | If true, the nameplate of the custom mob is permanently visible. |
| `AttackSpeed` | Double | *Vanilla* | Sets the base attack speed of the mob. |
| `VisibleByDefault` | Boolean | `true` | Set to false to spawn the mob invisible. |
| `Invisible` | Boolean | `false` | Sets the permanent invisibility effect on the mob. |
| `Collidable` | Boolean | `true` | Sets whether the mob has entity collisions enabled. |
| `DigOutOfGround` | Boolean | `false` | Teleports the mob 2 blocks up if it starts taking suffocation damage. |
| `Despawn` | String | `true` | Despawn policies: `true` / `NORMAL`, `NEVER` / `PERSISTENT` (prevents range-based despawning). |
| `FollowRange` | Integer | `32` | The range in blocks within which the mob targets/tracks players. |
| `Glowing` | Boolean | `false` | Sets whether the mob glows permanently. |
| `HealOnReload` | Boolean | `false` | Allows the mob to heal back to full when the chunk loads. |
| `Hidden` | Boolean | `false` | If true, hides the mob from commands or listing menus. |
| `Invincible` | Boolean | `false` | Makes the mob completely invulnerable to all damage. |
| `Interactable` | Boolean | `true` | If false, cancels player interaction with this mob. |
| `LockPitch` | Boolean | `false` | Lock head pitch movement. |
| `KnockbackResistance` | Double | `0.0` | Resistance percentage from `0.0` (0%) to `1.0` (100%). |
| `MaxCombatDistance` | Integer | `256` | Prevents players further than this distance from damaging the mob. |
| `MovementSpeed` | Double | `0.2` | The speed attribute of the mob. Values above `1.0` are extremely fast. |
| `NoAI` | Boolean | `false` | Sets whether the mob has AI. If false, the mob remains stationary. |
| `NoDamageTicks` | Integer | `10` | The ticks of invulnerability invoker gets after taking damage. |
| `NoGravity` | Boolean | `false` | Disables gravity for the mob. |
| `PassthroughDamage` | Boolean | `false` | Redirects damage to the parent sumonner if applicable. |
| `PreventItemPickup` | Boolean | `true` | Stops the mob from picking up ground items. |
| `PreventLeashing` | Boolean | `false` | Prevents a leash from being attached to the mob. |
| `PreventMobKillDrops` | Boolean | `false` | Prevents victim drops if they are killed by this mob. |
| `PreventOtherDrops` | Boolean | `false` | Prevents the mob from dropping its own vanilla loot tables upon death. |
| `PreventRandomEquipment` | Boolean | `false` | Prevents natural vanilla equipment spawning. |
| `PreventRenaming` | Boolean | `true` | Prevents players from renaming the mob using name tags. |
| `PreventSunburn` | Boolean | `false` | Prevents zombies and skeletons from burning in the daylight. |
| `PreventTransformation` | Boolean | `false` | Prevents the mob from converting to other variants (e.g., zombie to drowned). |
| `PreventVanillaDamage` | Boolean | `false` | Cancels regular vanilla attack damage from the mob (skills will still cast). |
| `Scale` | Double | `-1.0` | Sets the visual scale (size) of the mob (1.21+ attribute support). |
| `Silent` | Boolean | `false` | Mutes all vanilla sounds produced by the mob. |
| `RandomizeProperties` | Boolean | `true` | Enables/disables vanilla random spawn variations. |

---

## Specific / Group-Specific Options

These options apply only to specific Minecraft entity classes and will be ignored on others.

### Breedables & Ageables
*Applies to Cows, Sheep, Pigs, Chickens, Wolves, Cats, Rabbits, etc.*

- **`Age`** (Integer): Set numerical age. Use `-1` for a baby, `1` for an adult.
- **`AgeLock`** (Boolean): Locks the age to prevent the baby from naturally growing up.
- **`Adult`** (Boolean): Set adult status directly.
- **`Baby`** (Boolean): Set baby status directly.

### Colorables
*Applies to Sheep, Wolves, Llamas, Cats*

- **`Color`** (String): Sets wool color (Sheep) or collar color (Wolves, Cats). Supports standard dye names (e.g. `RED`, `LIME`, `BLUE`).

### Slimes & Magma Cubes
- **`Size`** (Integer): Sets the size scale of the slime (e.g. `1` to `10`).
- **`PreventSlimeSplit`** (Boolean): Prevents the slime/magma cube from splitting into smaller ones upon death.

### Creepers
- **`ExplosionRadius`** (Integer): Sets the blast power radius.
- **`FuseTicks`** (Integer): Ticks before exploding.
- **`SuperCharged`** (Boolean): Spawns the creeper powered (charged with lightning overlay).
- **`PreventSuicide`** (Boolean): Prevents the creeper from dying during its explosion.

### Armor Stands
- **`CanMove`** (Boolean): Sets if the armor stand can move.
- **`CanTick`** (Boolean): Sets if the armor stand ticks.
- **`HasArms`** (Boolean): Displays arms.
- **`HasBasePlate`** (Boolean): Toggles the bottom stone base plate.
- **`Small`** (Boolean): Spawns the small variant.
- **`Marker`** (Boolean): Makes the stand a marker (completely non-interactable).
- **`ItemHead` / `ItemBody` / `ItemLegs` / `ItemFeet` / `ItemHand` / `ItemOffhand`** (String): Equip custom keys from YueMiLibs directly onto the stand.

### Neutral mobs & Bees
- **`Anger`** (Integer): Ticks of anger duration.
- **`HasNectar`** (Boolean): If the bee carries nectar.
- **`HasStung`** (Boolean): If the bee has stung.

### Saddleable Mobs (Camel, Pig, Strider, Horses)
- **`Saddled`** (Boolean): Spawns the entity saddled.

### Cats & Foxes
- **`CatType`** (String): Cat variant (e.g. `BLACK`, `SIAMESE`, `CALICO`).
- **`FoxType`** (String): Fox variant (`RED` or `SNOW`).

### Frogs
- **`Variant`** (String): Frog variant (`WARM`, `COLD`, `TEMPERATE`).

### Hoglins & Piglins
- **`ImmuneToZombification`** (Boolean): Prevents conversion to Zoglins/Zombie Piglins.
- **`Huntable`** (Boolean): Allows/prevents Hoglins from being hunted by Piglins.
- **`AbleToHunt`** (Boolean): Allows/prevents Piglins from hunting.

### Villagers & Zombie Villagers
- **`Profession`** (String): Profession type (e.g. `MASON`, `FARMER`, `CLERIC`).
- **`Type`** (String): Villager biome variant (e.g. `DESERT`, `PLAINS`, `SNOW`).
- **`Level`** (Integer): Profession level (`1` to `5`).
