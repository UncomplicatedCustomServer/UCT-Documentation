---
icon: people-group
---

# Defining a Team

You don't need to rely solely on YAML configs. You can register teams programmatically from your own plugin.

### The `Team` Class

The `Team` class is a pure **data container**. It holds the configuration but does not handle logic.

```csharp
public void RegisterMyCoolTeam()
{
    // 1. Create the Team Definition
    var myTeam = new Team
    {
        Id = 99, // Must be unique
        Name = "Cyber-Squad",
        SpawnChance = 50,
        MinPlayers = 2,
        MaxSpawns = 1,
        SpawnConditions = new SpawnData
        {
            SpawnWave = WaveType.NtfWave,
            SpawnDelay = 0f
        },
        IsCassieAnnouncementEnabled = true,
        CassieMessage = "CYBER SQUAD HAS ENTERED",
        IsNoisy = true
    };

    // 2. Define Custom Roles
    // You DO NOT need to manually register these roles to UCR. 
    // UCT handles registration automatically via the JIT (Just-In-Time) system.
    var sniperRole = new UncomplicatedCustomRole
    {
        Id = 101, // Unique Role ID
        Role = PlayerRoles.RoleTypeId.NtfSpecialist,
        Name = "Cyber Sniper",
        MaxPlayers = 1,
        Priority = RolePriority.First,
        IsGodmodeEnabled = false,
        DropInventoryOnDeath = true
    };

    // 3. Add Role to Team
    myTeam.Roles.Add(sniperRole);

    // 4. Register the Team to UCT
    Team.Register(myTeam);
}
```

**Note:** To remove a team, use `Team.Unregister(myTeam);.`

### Smart Role Registration (JIT)

In previous versions, you had to manually register roles to UCR and worry about plugin load order. **Not anymore.**

UCT v2.0 introduces **Just-In-Time (JIT) Registration**.

* You simply define the `UncomplicatedCustomRole` and add it to your Team.
* When the team spawns, UCT checks if the role is registered.
* If it's missing, **UCT registers it automatically** instantly before spawning the player.

> **Developer Note:** You can still register roles manually if you wish, but it is no longer required for the team to function.

### Handling Reloads

When an administrator executes the `uct reload` command, **all teams (including yours) are wiped from memory** to allow fresh config loading.

To ensure your code-defined team persists after a reload, you **must** subscribe to the `DefinitionsLoaded` event.

```csharp
public class MyPlugin
{
    public override void Enable()
    {
        // 1. Register immediately on startup
        RegisterMyCoolTeam();

        // 2. Re-register automatically when UCT reloads configs
        UCTEvents.DefinitionsLoaded += RegisterMyCoolTeam;
    }

    public override void Disable()
    {
        UCTEvents.DefinitionsLoaded -= RegisterMyCoolTeam;
    }

    public void RegisterMyCoolTeam()
    {
        // Safety Check: Ensure we don't add the team twice
        if (Team.List.Any(t => t.Name == "Cyber-Squad")) return;

        var myTeam = new Team
        {
            Id = 99,
            Name = "Cyber-Squad"
        };

        Team.Register(myTeam);
    }
}
```
