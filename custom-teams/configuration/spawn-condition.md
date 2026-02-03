---
icon: calculator-simple
---

# Spawn Condition

Spawn Condition acts as the core of UCT, defining the configuration for how, where, and when a Custom Team spawns. It is characterized by a large number of events (Spawn Waves); e.g., `RoundStarted` triggers a spawn when the round begins.

Please note that certain options, like `UsedItem (used_item)`, become active only when the corresponding Spawn Wave is selected.

**Important:** Defining position and/or rotation is mandatory for all Spawn Waves except `NtfWave` and `ChaosWave`. Leaving coordinates at zero will result in an error, unless using `NtfWave` or `ChaosWave`, which default to their vanilla spawn locations.

## Spawn Condition

The **Spawn Condition** object should look like this:

```yml
  spawn_conditions:
    spawn_wave: NtfWave
    spawn_position:
      x: 0
      y: 0
      z: 0
    spawn_rotation:
      x: 0
      y: 0
      z: 0
    after_team_spawn: 0
    after_team_death: 0
    required_engaged_generators: 1
    used_item: None
    target_scp: None
    is_scp0492_counted_as_scp: false
    required_alive_roles: []
    roles_affected_on_round_start: []
    spawn_delay: 0
```

## Spawn Wave

**Configuration element name:** `spawn_wave` \
**Type:**  [#wave-type](../../syntax/enums.md#wave-type "mention")

Determines which **Wave Type** is used to spawn Custom Team.

## Spawn Position

**Configuration element name:** `spawn_position` \
**Type: `Vector3`**

Enables spawning the Custom Team at specific `x`, `y`, and `z` coordinates.

## Spawn Rotation

**Configuration element name:** `spawn_rotation` \
**Type: `Vector3`**

Enables setting the direction in which Custom Team members will look upon spawning.

## After Team Spawn

**Configuration element name:** `after_team_spawn`\
**Type: `uint32`**

Spawns the Custom Team after another Custom Team spawns.\
**Note:** Requires the Spawn Wave to be set to `TeamDependent`.

## After Team Death

**Configuration element name:** `after_team_death`\
**Type: `uint32`**

Spawns the Custom Team after the elimination of another Custom Team.\
**Note:** Requires the Spawn Wave to be set to `TeamDependent`.

## Required Engaged Generators

**Configuration element name:** `required_engaged_generators`\
**Type: `int32`**&#x20;

Spawns the Custom Team after a specific number of generators have been activated.\
**Note:** Requires the Spawn Wave to be set to `AfterGeneratorActivated`.

## Used Item

**Configuration element name:** `used_item`\
**Type: `string`**

Triggers the Custom Team spawn upon the use of a specific item. You may specify the item using the `ItemType` Enum or by inputting an EXILED Custom Item ID; both methods are accepted.\
**Note:** Requires the Spawn Wave to be set to `UsedItem`.

## Target Scp

**Configuration element name:** `target_scp`\
**Type: `string`**

Triggers a Custom Team spawn upon the death of a specific SCP role (from the `RoleTypeId` Enum). Alternatively, setting this to `SCPs` (Team name) will trigger the spawn when any SCP is killed.\
**Note:** Requires the Spawn Wave to be set to `ScpDeath`.

## Is Scp 0492 Counted As Scp

**Configuration element name:** `is_scp_0492_counted_as_scp`\
**Type: `bool`**

Determines whether SCP-049-2 is included as an SCP. This is useful when `TargetSCP` is set to `SCPs`.

## Required Alive Roles

**Configuration element name:** `required_alive_roles`\
**Type: `List<RoleTypeId>`**

A list of `RoleTypeId` Enum that must be alive for the Custom Team to spawn.

## Roles Affected On Round Start

**Configuration element name:** `roles_affected_on_round_start`\
**Type: `List<RoleTypeId>`**

Defines which starting roles can be converted into this team. At the start of the round, the plugin will randomly select players from these roles to respawn as Custom Team.\
**Note:** Requires the Spawn Wave to be set to `RoundStarted`.

## Spawn Delay

**Configuration element name:** `spawn_delay`\
**Type:** `float`

Configures the delay before the Custom Team spawns. A value of 0 results in an immediate spawn; any other value defines the delay in seconds.\
**Note:** This setting does not apply to `NtfWave` or `ChaosWave`.
