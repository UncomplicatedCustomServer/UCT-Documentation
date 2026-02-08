---
icon: person-running-fast
---

# Runtime Interaction

When a `Team` (Definition) is spawned, it becomes a `SummonedTeam` (Runtime Instance). This object holds the actual players and live status.

#### Retrieving Active Teams

```cs
// Get all currently active custom teams
foreach (var team in SummonedTeam.List)
{
    Logger.Info($"Team {team.Definition.Name} has {team.Members.Count} members.");
}

// Find a team by its Unique Runtime ID
SummonedTeam specificTeam = SummonedTeam.Get("some-guid-id");
```

#### Properties

* `Members`: List of `SummonedCustomRole` (Wrapper around Player + Role info).
* `IsEliminated`: Boolean flag indicating if the team has been wiped out.
* `SpawnTime`: Unix timestamp of when the team spawned.
* `Definition`: Access the original config (`Team` object) via `summonedTeam.Definition`.
