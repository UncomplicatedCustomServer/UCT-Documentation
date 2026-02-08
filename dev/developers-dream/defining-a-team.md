---
icon: people-group
---

# Defining a Team

You don't need to rely solely on YAML configs. You can register teams programmatically from your own plugin.

#### The `Team` Class

The `Team` class is a pure data container. It holds the configuration but does not handle logic.

```cs
public void RegisterMyCoolTeam()
{
    // 1. Create the Team Definition
    var myTeam = new Team
    {
        Id = 99, // Must be unique
        Name = "Cyber-Squad",
        SpawnChance = 50, // 50% chance
        MinPlayers = 2,
        MaxSpawns = 1, // Only once per round
        
        // Setup Spawn Conditions
        SpawnConditions = new SpawnData
        {
            SpawnWave = WaveType.NtfWave, // Replaces NTF
            SpawnDelay = 0
        },

        // Setup Announcement
        IsCassieAnnouncementEnabled = true,
        CassieMessage = "CYBER SQUAD HAS ENTERED THE FACILITY",
        IsNoisy = true
    };

    // 2. Add Roles to the Team
    myTeam.Roles.Add(new UncomplicatedCustomRole
    {
        Id = 1, // Unique Role ID
        Role = PlayerRoles.RoleTypeId.NtfCaptain,
        MaxPlayers = 1,
        Priority = RolePriority.First,
        IsGodmodeEnabled = false
    });

    // 3. Register it to the UCT System
    Team.Register(myTeam);
}
```

**Note:** To remove a team, use `Team.Unregister(myTeam);`.
