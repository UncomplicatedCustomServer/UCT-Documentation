---
icon: up-right-from-square
---

# Spawn Data Extensions

With the introduction of the modular **Settings** system in `SpawnData`, properties like `TargetScp` or `SpawnPosition` are no longer directly accessible as class properties. They are stored in a Dictionary.

To safely retrieve these values in your code, you **must** use the provided Extension Methods found in `SpawnDataExtensions` class.

## Generic Retrieval

If you need to get a raw value from the settings dictionary safely:

```csharp
// GetSetting<T>(key, defaultValue)
int myValue = team.SpawnConditions.GetSetting<int>("my_custom_key", 0);
```

## Built-in Helpers

We provide strong-typed helper methods for all standard UCT settings.

#### **Positioning**

```csharp
// Returns Vector3 based on pos_x, pos_y, pos_z (or 0,0,0)
Vector3 pos = team.SpawnConditions.GetSpawnPosition();

// Returns Vector3 based on rot_x, rot_y, rot_z (or 0,0,0)
Vector3 rot = team.SpawnConditions.GetSpawnRotation();
```

## **Wave-Specific Data**

#### Generators:

```csharp
// Gets 'required_engaged'
int required = team.SpawnConditions.GetRequiredGenerators();
```

#### Team Dependencies:

```csharp
// Gets 'after_team_spawn' ID
uint parentSpawnId = team.SpawnConditions.GetAfterTeamSpawn();

// Gets 'after_team_death' ID
uint parentDeathId = team.SpawnConditions.GetAfterTeamDeath();
```

#### Items:

```csharp
// Gets 'used_item' as ItemType
ItemType item = team.SpawnConditions.GetUsedItem();

// Gets 'custom_item_id' (int?)
int? customId = team.SpawnConditions.GetCustomItemId();
```

#### SCP Death:

```csharp
// Gets 'target_scp' (returns "None", "Scp173", "SCPs", etc.)
string target = team.SpawnConditions.GetTargetScp();

// Gets 'count_zombies' bool
bool countZombies = team.SpawnConditions.IsScp0492CountedAsScp();
```

#### Roles & Lists:

```csharp
// Gets 'required_roles' list
List<RoleTypeId> required = team.SpawnConditions.GetRequiredAliveRoles();

// Gets 'affected_roles' list (RoundStarted)
List<RoleTypeId> affected = team.SpawnConditions.GetRolesAffectedOnRoundStart();
```
