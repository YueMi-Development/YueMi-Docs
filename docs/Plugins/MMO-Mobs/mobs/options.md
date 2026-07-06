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

| Option | Entity Group / Mob Type | Type | Description |
| :--- | :--- | :--- | :--- |
| `Age` | Breedables / Ageables | Integer | Sets the numerical age. Use `-1` for a baby, `1` for an adult. |
| `AgeLock` | Breedables / Ageables | Boolean | Locks the age to prevent the baby from naturally growing up. |
| `Adult` | Breedables / Ageables | Boolean | Sets the adult status directly. |
| `Baby` | Breedables / Ageables | Boolean | Sets the baby status directly. |
| `Color` | Sheep / Wolves / Llamas | String | Sets wool color (Sheep) or collar color (Wolves, Cats). Supports dye colors (e.g., `RED`, `LIME`). |
| `Size` | Slimes & Magma Cubes | Integer | Sets the size scale of the slime/magma cube. |
| `PreventSlimeSplit` | Slimes & Magma Cubes | Boolean | Prevents splitting into smaller slimes/magma cubes upon death. |
| `ExplosionRadius` | Creepers | Integer | Sets the explosion power radius. |
| `FuseTicks` | Creepers | Integer | Ticks before exploding. |
| `SuperCharged` | Creepers | Boolean | Spawns the creeper powered (charged with lightning overlay). |
| `PreventSuicide` | Creepers | Boolean | Prevents the creeper from dying during its explosion. |
| `CanMove` | Armor Stand | Boolean | Sets if the armor stand can move. |
| `CanTick` | Armor Stand | Boolean | Sets if the armor stand ticks. |
| `HasArms` | Armor Stand | Boolean | Displays arms. |
| `HasBasePlate` | Armor Stand | Boolean | Toggles the bottom stone base plate. |
| `Small` | Armor Stand | Boolean | Spawns the small variant of the armor stand. |
| `Marker` | Armor Stand | Boolean | Makes the armor stand a marker (completely non-interactable). |
| `ItemHead`, `ItemBody`, `ItemLegs`, `ItemFeet`, `ItemHand`, `ItemOffhand` | Armor Stand | String | Equip custom keys from YueMiLibs directly onto the stand. |
| `Anger` | Bees | Integer | Ticks of anger duration. |
| `HasNectar` | Bees | Boolean | If the bee is carrying pollen. |
| `HasStung` | Bees | Boolean | If the bee has stung an entity. |
| `Saddled` | Saddleable Mobs | Boolean | Spawns the entity saddled (Camel, Pig, Strider, Horses). |
| `CatType` | Cats | String | Cat variant (e.g. `BLACK`, `SIAMESE`, `CALICO`). |
| `FoxType` | Foxes | String | Fox variant (`RED` or `SNOW`). |
| `Variant` | Frogs / Wolves / Chickens | String | Frog/Wolf biome variant (e.g., `WARM`, `COLD` for Frogs; `black`, `chestnut` for Wolves). |
| `ImmuneToZombification` | Hoglins / Piglins | Boolean | Prevents conversion to Zoglins/Zombie Piglins. |
| `Huntable` | Hoglins | Boolean | Allows/prevents Hoglins from being hunted by Piglins. |
| `AbleToHunt` | Piglins | Boolean | Allows/prevents Piglins from hunting. |
| `Profession` | Villagers / Zombie Villagers | String | Profession type (e.g. `MASON`, `FARMER`, `CLERIC`). |
| `Type` | Villagers | String | Villager biome variant (e.g. `DESERT`, `PLAINS`, `SNOW`). |
| `Level` | Villagers | Integer | Profession level (`1` to `5`). |

