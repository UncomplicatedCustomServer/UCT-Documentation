---
icon: calculator-simple
---

# Spawn Condition

Spawn Condition acts as the core of UCT, defining the configuration for how, where, and when a Custom Team spawns. The system has been completely overhauled to be modular. Instead of a large list of unused parameters, we now use a clean `settings` dictionary. You only need to define the settings relevant to your chosen `spawn_wave`.

**The Base Structure**

Every team must have a `spawn_conditions` block. Inside, you define the Wave Type, the Delay, and the specific Settings.

```yaml
spawn_conditions:
  spawn_wave: NtfWave # The trigger event
  spawn_delay: 0      # Delay in seconds
  settings:           # Dynamic settings specific to the Wave
    # ... module specific settings go here ...
```

Below is the list of available modules you can use inside the `settings` list, depending on your `spawn_wave`.



## ⚠️ **Important**: YAML Indentation & Spaces

YAML files are **extremely sensitive to indentation (spaces)**. The structure is defined by how many spaces are before each line.

The `settings` block must be indented **inside** the `spawn_conditions` block. If you place `settings` at the same level as `spawn_conditions` (too far to the left), the plugin will not see your settings and will load **default values**.

**❌ INCORRECT (Settings are outside):**

```yaml
spawn_conditions:
  spawn_wave: RoundStarted
  spawn_delay: 0
settings:               # <--- WRONG! This is not part of spawn_conditions
  pos_x: 12.5           # These values will be IGNORED
  pos_y: 100.0
```

✅ CORRECT (Settings are nested inside):

```yml
spawn_conditions:
  spawn_wave: RoundStarted
  spawn_delay: 0
  settings:             # <--- CORRECT! Indented to be inside spawn_conditions
    pos_x: 12.5         # <--- Also indented inside settings
    pos_y: 100.0
```

> Tip: Always use 2 spaces for each level of indentation. Do not use Tab characters.

### &#x20;**Custom Position & Rotation**

Supported Waves: `RoundStarted`, `AfterWarhead`, `AfterDecontamination`, `TeamDependent`, etc.

Note: `NtfWave` and `ChaosWave` use vanilla spawn points by default, so these settings are optional for them.

<table data-header-hidden><thead><tr><th width="249">Key</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td><code>pos_x</code></td><td>float</td><td>The X coordinate of the spawn position.</td></tr><tr><td><code>pos_y</code></td><td>float</td><td>The Y coordinate of the spawn position.</td></tr><tr><td><code>pos_z</code></td><td>float</td><td>The Z coordinate of the spawn position.</td></tr><tr><td><code>rot_x</code></td><td>float</td><td>The X rotation (pitch).</td></tr><tr><td><code>rot_y</code></td><td>float</td><td>The Y rotation (yaw/direction).</td></tr><tr><td><code>rot_z</code></td><td>float</td><td>The Z rotation (roll).</td></tr></tbody></table>

Example:

```yaml
  settings:
    pos_x: 12.5
    pos_y: 100.0
    pos_z: -45.0
    rot_y: 90.0
```



### **SCP Death (`ScpDeath`)**

Triggers when a specific SCP dies.

| **Key**         | **Type** | **Description**                                                                            |
| --------------- | -------- | ------------------------------------------------------------------------------------------ |
| `target_scp`    | string   | The RoleTypeId of the SCP (e.g., `Scp173`) or `SCPs` for any SCP death.                    |
| `count_zombies` | bool     | If `target_scp` is `SCPs`, should SCP-049-2 (Zombies) trigger the spawn? Default: `false`. |

Example:

```yml
spawn_conditions:
  spawn_wave: ScpDeath
  spawn_delay: 5
  settings:
    target_scp: Scp173
```



### **Used Item (`UsedItem`)**

Triggers when a player uses a specific item.

| **Key**          | **Type** | **Description**                             |
| ---------------- | -------- | ------------------------------------------- |
| `used_item`      | string   | The ItemType enum name (e.g., `Medkit`).    |
| `custom_item_id` | int      | Alternatively, the ID of a UCI Custom Item. |

Example:

```yaml
spawn_conditions:
  spawn_wave: UsedItem
  settings:
    used_item: Painkillers
    # OR
    custom_item_id: 12
```



### **Generators (`AfterGeneratorActivated`)**

Triggers after a specific number of generators are engaged.

| **Key**            | **Type** | **Description**                                    |
| ------------------ | -------- | -------------------------------------------------- |
| `required_engaged` | int      | Number of generators required to trigger the team. |

Example:

```yml
spawn_conditions:
  spawn_wave: AfterGeneratorActivated
  settings:
    required_engaged: 2
```



### **Round Start (`RoundStarted`)**

Converts specific roles into the Custom Team at the beginning of the round.

| **Key**          | **Type** | **Description**                                                            |
| ---------------- | -------- | -------------------------------------------------------------------------- |
| `affected_roles` | List     | A list of RoleTypeIds that can be converted (e.g., `[ClassD, Scientist]`). |

Example:

```yml
spawn_conditions:
  spawn_wave: RoundStarted
  settings:
    affected_roles:
      - ClassD
      - Scientist
```



### **Team Dependencies (`TeamDependent`)**

Triggers when another Custom Team spawns or is eliminated.

| **Key**            | **Type** | **Description**                                          |
| ------------------ | -------- | -------------------------------------------------------- |
| `after_team_spawn` | uint     | The ID of the team that must spawn to trigger this team. |
| `after_team_death` | uint     | The ID of the team that must die to trigger this team.   |

Example:

```yml
spawn_conditions:
  spawn_wave: TeamDependent
  spawn_delay: 10
  settings:
    after_team_death: 1 # Spawns when Team ID 1 dies
```

### &#x20; **Global Filters (Optional)**

These keys can be used with any wave type to add extra restrictions.

| **Key**          | **Type** | **Description**                                                                |
| ---------------- | -------- | ------------------------------------------------------------------------------ |
| `required_roles` | List     | A list of RoleTypeIds that MUST be alive on the server for this team to spawn. |

Example:

```yml
  settings:
    target_scp: Scp096
    required_roles:
      - NtfCaptain # Only spawn if an NTF Captain is alive
```
