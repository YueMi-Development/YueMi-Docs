---
title: Targeters
sidebar_position: 2
---

# Skill Targeters

This is a list of all available skill targeters in MMO Mechanics, grouped by their target outputs. Click on any targeter name to see its options and details.

---

## Single-Entity Targeters

Targets a single entity.

| Targeter | Aliases / Shorthands | Description |
| :--- | :--- | :--- |
| **[Caster / Self](./details/self.md)** | `self`, `caster`, `boss`, `mob` | Targets the caster of the mechanic/skill itself. |
| **[CasterTarget / Target](./details/target.md)** | `target`, `t` | Targets the entity that the caster is currently looking at or targeting. |
| **[Trigger](./details/trigger.md)** | `trigger` | Targets the entity that triggered the skill. |
| **[NearestPlayer](./details/nearestplayer.md)** | `nearestplayer` | Targets the single nearest player in a radius around the caster. |
| **[Owner](./details/owner.md)** | `owner`, `wolfowner` | Targets the entity that owns the caster. |
| **[Parent](./details/parent.md)** | `parent`, `summoner` | Targets the parent or summoner entity of the caster. |
| **[Mount](./details/mount.md)** | `mount` | Targets the entity that the caster is riding (their mount). |
| **[Passenger](./details/passenger.md)** | `passenger` | Targets the entity that is riding on top of the caster. |
| **[PlayerByName](./details/playerbyname.md)** | `playerbyname`, `specificplayer` | Targets a specific player online on the server by their name. |
| **[Uuid](./details/uuid.md)** | `uuid`, `uniqueidentifier` | Targets a specific entity by its unique UUID. |
| **[Near](./details/near.md)** | `near` | Targets entities within a close proximity to the caster. |

---

## Multi-Entity Targeters

Targets multiple entities.

| Targeter | Aliases / Shorthands | Description |
| :--- | :--- | :--- |
| **[LivingInCone](./details/livingincone.md)** | `livingincone`, `entitiesincone`, `livingentitiesincone`, `leic`, `eic` | Targets living entities inside a cone sector in front of the caster. |
| **[LivingInWorld](./details/livinginworld.md)** | `livinginworld`, `eiw` | Targets all living entities in the same world as the caster. |
| **[NotLivingNearOrigin](./details/notlivingnearorigin.md)** | `notlivingnearorigin`, `nonlivingnearorigin`, `nlno` | Targets non-living entities within a radius around origin. |
| **[PlayersInRadius](./details/playersinradius.md)** | `playersinradius`, `pir` | Targets all players within a specified radius. |
| **[MobsInRadius](./details/mobsinradius.md)** | `mobsinradius`, `mir`, `mobsnearorigin` | Targets monsters or vanilla mobs of specified types. |
| **[EntitiesInRadius](./details/entitiesinradius.md)** | `entitiesinradius`, `livingentitiesinradius`, `livinginradius`, `allinradius`, `eir`, `entitiesnearorigin`, `eno` | Targets all living entities within a specified radius. |
| **[EntitiesInRing](./details/entitiesinring.md)** | `entitiesinring`, `eirr`, `entitiesinringnearorigin`, `erno` | Targets all living entities within a ring boundary. |
| **[PlayersInWorld](./details/playersinworld.md)** | `playersinworld`, `world` | Targets all players currently in the same world as the caster. |
| **[PlayersOnServer](./details/playersonserver.md)** | `playersonserver`, `server`, `everyone` | Targets all players online on the server. |
| **[PlayersInRing](./details/playersinring.md)** | `playersinring` | Targets players located within a ring boundary. |
| **[PlayersNearOrigin](./details/playersnearorigin.md)** | `playersnearorigin`, `pno` | Targets all players within a specified radius around the origin. |
| **[TrackedPlayers](./details/trackedplayers.md)** | `trackedplayers`, `tracked` | Targets all players currently tracking the caster. |
| **[Children / Summons](./details/children.md)** | `children`, `child`, `summons` | Targets any tethers/pets of the caster. |
| **[Siblings](./details/siblings.md)** | `siblings`, `sibling`, `brothers`, `sisters` | Targets sibling summons sharing the same owner. |
| **[ItemsInRadius](./details/itemsnearorigin.md)** | `itemsnearorigin`, `itemsinradius`, `iir` | Targets dropped items on the ground within a specified radius. |

---

## Single-Location Targeters

Targets a single block or coordinate location.

| Targeter | Aliases / Shorthands | Description |
| :--- | :--- | :--- |
| **[SelfLocation](./details/selflocation.md)** | `selflocation`, `casterlocation`, `bosslocation`, `moblocation` | Targets the current location of the caster. |
| **[SelfEyeLocation](./details/selfeyelocation.md)** | `selfeyelocation`, `eyedirection`, `castereyelocation`, `bosseyelocation`, `mobeyelocation` | Targets the eye location of the caster. |
| **[Forward](./details/forward.md)** | `forward` | Targets a location directly in front of the caster's looking direction. |
| **[ProjectileForward](./details/projectileforward.md)** | `projectileforward` | Targets a location directly in front of the casting projectile. |
| **[TargetLocation](./details/targetlocation.md)** | `targetlocation`, `targetloc`, `tl` | Targets the location of the caster's current target. |
| **[TargetPredictedLocation](./details/targetpredictedlocation.md)** | `targetpredictedlocation`, `targetpredictedloc`, `tpl`, `predictedtargetlocation` | Targets the predicted location of the target based on movement. |
| **[TriggerLocation](./details/triggerlocation.md)** | `triggerlocation` | Targets the location of the entity/event that triggered the skill. |
| **[SpawnLocation](./details/spawnlocation.md)** | `spawnlocation`, `casterspawnlocation` | Targets the spawn location of the world. |
| **[CoordinateLocation](./details/location.md)** | `location`, `origin`, `source` | Targets a specific set of coordinates (X, Y, Z). |
| **[ObstructingBlock](./details/obstructingblock.md)** | `obstructingblock` | Targets the solid block blocking the caster's path. |
| **[TargetBlock](./details/targetblock.md)** | `targetblock` | Targets the block that the caster is currently looking at. |
| **[VariableLocation](./details/variablelocation.md)** | `variablelocation`, `varlocation` | Targets the location stored in a specified variable. |
| **[HighestBlock](./details/highestblock.md)** | `highestblock` | Targets the highest solid block directly above or below origin. |
| **[PlayerLocationByName](./details/playerlocationbyname.md)** | `playerlocationbyname` | Targets the current location of a specific player by name. |
| **[EscapeLocation](./details/escapelocation.md)** | `escapelocation` | Targets a nearby safe escape teleport location. |

---

## Multi-Location Targeters

Targets a collection of coordinate locations or shape points.

| Targeter | Aliases / Shorthands | Description |
| :--- | :--- | :--- |
| **[ForwardWall](./details/forwardwall.md)** | `forwardwall` | Generates a wall-like plane grid of locations in front of the caster. |
| **[PlayerLocationsInRadius](./details/playerlocationsinradius.md)** | `playerlocationsinradius`, `plir` | Targets the locations of all players within a specified radius. |
| **[Pin](./details/pin.md)** | `pin` | Targets the location marked by a pin in the current context. |
| **[Ring](./details/ring.md)** | `ring`, `ringaroundorigin`, `ringorigin`, `rao` | Generates points forming a ring of target locations. |
| **[RandomRingPoint](./details/randomringpoint.md)** | `randomringpoint` | Targets a random point location along a ring around the caster. |
| **[Cone](./details/cone.md)** | `cone` | Generates a list of locations forming a cone shape on the ground. |
| **[Sphere](./details/sphere.md)** | `sphere` | Generates point locations forming a sphere shell. |
| **[Rectangle](./details/rectangle.md)** | `rectangle`, `cube`, `cuboid` | Generates a 3D grid of target locations forming a cuboid outline. |
| **[RandomLocations](./details/randomlocations.md)** | `randomlocationsnearcaster`, `randomlocations`, `rlnc`, `randomlocationsnearorigin`, `rlo`, `randomlocationsorigin`, `rlno` | Targets random location coordinates in a radius. |
| **[BlocksNearOrigin](./details/blocksnearorigin.md)** | `blocksnearorigin`, `bno` | Targets all block locations in a radius around origin. |
