---
icon: ufo-beam
---

# Spawning Teams

You can force a spawn or evaluate RNG chances using the `TeamSpawner` service.

#### Force Spawn

This method automatically finds spectators, handles events, and spawns the team immediately.

```cs
// Find your team definition
Team myTeamDefinition = Team.List.FirstOrDefault(t => t.Name == "Cyber-Squad");

// Force spawn immediately
if (myTeamDefinition != null)
{
    SummonedTeam activeTeam = TeamSpawner.SpawnSpecificTeam(myTeamDefinition);
    
    if (activeTeam != null)
    {
        Logger.Info($"Spawned {activeTeam.Members.Count} players!");
    }
}
```

#### Evaluate RNG (Manual Wave Handling)

If you want to simulate a wave spawn (like checking `SpawnChance` and `AllowConcurrentSpawns`) without necessarily spawning them right away:

```cs
// Get a list of teams that "won" the RNG roll for this wave type
List<Team> winners = TeamSpawner.EvaluateSpawn(WaveType.AfterDecontamination);

foreach (var team in winners)
{
    // You can spawn them now
    TeamSpawner.SpawnSpecificTeam(team);
}
```

