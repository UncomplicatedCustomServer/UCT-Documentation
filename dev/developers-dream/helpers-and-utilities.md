---
icon: circle-question
---

# Helpers & Utilities

We provide extension methods to make your life easier.

### Check if Player is in Custom Team

```cs
Player player = Player.Get(playerId);

// Returns the SummonedTeam instance or null
SummonedTeam team = player.GetCustomTeam(); 

if (team != null) 
{
    Logger.Info($"{player.Nickname} is part of {team.Definition.Name}");
}
```

### Check Relations (Allies/Enemies)

Easily check if two players should be friendly, based on the `AlliedTeams` config in the Team definition.

```cs
Player playerA = Player.Get(playerId);
Player playerB = Player.Get(playerId);

if (playerA.IsCustomTeamAlly(playerB))
{
    // ...
}
```

### Audio Service

You can trigger the custom team's announcement/music manually if needed:

```cs
// Plays Cassie or/and Custom Music defined in the Team config
AudioService.PlayTeamAnnouncement(myTeamDefinition); 
```

### Team Communication

Need to send a private message to the whole squad? Use the built-in helper.

```cs
var team = SummonedTeam.List.First();

// Sends a Broadcast
team.BroadcastToMembers(5, "Retreat to Surface!");

// Sends a Hint
team.BroadcastToMembers(5, "Objective Updated", isHint: true);
```

### **Reloading Configuration**

You can trigger a full reload of the plugin configuration programmatically.

```csharp
// Reloads all UCT configurations
TeamExtensions.Reload();
```

**Wave Validation**

Check if a specific `WaveType` requires manual coordinate configuration (Position).

```cs
// Returns true if the wave requires pos_x/y/z
bool requiresCoords = TeamExtensions.IsCustomPositionWave(WaveType.RoundStarted); 

if (requiresCoords)
{
    // ... logic to ensure coordinates are present
}
```

### &#x20;Metadata System

The **Metadata System** allows you to attach arbitrary data to a running `SummonedTeam` instance. This is perfect for creating objectives without managing your own external Dictionaries.

#### Storing Data

Let's say you want to track "Kill Count" for a specific Squad.<br>

```csharp
UCTEvents.TeamSpawned += OnSpawn;

void OnSpawn(TeamSpawnedEventArgs ev)
{
    // Initialize a custom counter inside the team object
    ev.SummonedTeam.SetData("kill_count", 0);
}
```

### Retrieving & Modifying Data

Later in your plugin, when a kill happens:

```cs
public void OnPlayerDeath(PlayerDeathEventArgs ev)
{
    Player killer = ev.Attacker;
    SummonedTeam team = killer.GetCustomTeam();

    if (team != null && team.HasData("kill_count"))
    {
        // Get current value
        int currentKills = team.GetData<int>("kill_count");
        
        // Update value
        team.SetData("kill_count", currentKills + 1);
        
        Logger.Info($"{team.Definition.Name} now has {currentKills + 1} kills!");
    }
}
```

### Example: Custom Win Logic

Here is a full example of how to use the API to create a "VIP Escort" scenario where a custom team wins if they survive for 5 minutes.

```cs
public class VipModePlugin
{
    public void Init()
    {
        UCTEvents.TeamSpawned += OnTeamSpawned;
    }

    private void OnTeamSpawned(TeamSpawnedEventArgs ev)
    {
        if (ev.Team.Name == "VIP_Escort")
        {
            // Set the objective time (5 minutes from now)
            DateTime winTime = DateTime.UtcNow.AddMinutes(5);
            ev.SummonedTeam.SetData("win_time_ticks", winTime.Ticks);
            
            ev.SummonedTeam.BroadcastToMembers(10, "Protect the VIP for 5 minutes!");
        }
    }

    // Check every second (or inside a coroutine)
    private void CheckWinCondition()
    {
        foreach (var team in SummonedTeam.List)
        {
            if (team.HasData("win_time_ticks"))
            {
                long winTicks = team.GetData<long>("win_time_ticks");
                
                if (DateTime.UtcNow.Ticks >= winTicks && !team.IsEliminated)
                {
                    // WIN CONDITION MET
                    Server.SendBroadcast($"Team {team.Definition.Name} has escaped successfully!", 10);
                    Round.EndRound();
                }
            }
        }
    }
}
```

