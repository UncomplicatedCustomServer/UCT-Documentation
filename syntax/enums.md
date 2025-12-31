---
icon: square-poll-vertical
---

# Enums

Enums are a crucial element of UCT, serving to define configuration logic. They enable you to determine specific conditions, such as spawning a Custom Team upon Warhead detonation versus LCZ Decontamination. Without this system, customization would be minimal.

**Note:** For Enums like `RoleTypeId` (related to roles), please refer to: (placeholder).

Below you will find all Enums used in UCT that are necessary for configuration.



## Wave Type

**Used for:** `Spawn Wave`

```yaml
        None
        NtfWave
        ChaosWave
        AfterWarhead
        AfterDecontamination
        UsedItem
        RoundStarted
        ScpDeath
        TeamDependent
        AfterGeneratorActivated
```

#### Explanation:

* None - Undefined Wave type. Disables automatic spawning for this Custom Team, limiting it to manual spawns via the `uct spawn` command.
* NtfWave - Replaces the Nine-Tailed Fox spawn wave with this Custom Team.
* ChaosWave - Replaces the Chaos Insurgency spawn wave with this Custom Team.
* AfterWarhead - Spawns the Custom Team after the Warhead detonates.
* AfterDecontamination - Spawns the Custom Team after LCZ decontamination.
* UsedItem - Spawns the Custom Team after a specific item is used. This can be a base game item or an EXILED Custom Item.
* RoundStarted - Spawns the Custom Team after the round starts.
* ScpDeath - Spawns the Custom Team after an SCP dies. This can trigger on a specific SCP or the SCP team generally.
* TeamDependent - The Custom Team spawn depends on another Custom Team. It can spawn either after the other team spawns or after it is eliminated.
* AfterGeneratorActivated -Spawns the Custom Team after an SCP-079 Generator is activated.
