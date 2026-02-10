---
icon: calendar-days
---

# Events System

#### `TeamSpawning`

Fires before the team spawns.

* Use case: Cancel the spawn or modify the list of players.
* Arguments: `Team`, `PlayersToSpawn` (List\<Player>), `IsAllowed`.

```cs
UCTEvents.TeamSpawning += OnTeamSpawning;

void OnTeamSpawning(TeamSpawningEventArgs ev)
{
    if (ev.Team.Name == "GOC" && Round.Duration.TotalMinutes < 5)
    {
        ev.IsAllowed = false; // Block GOC in the first 5 minutes
    }
}
```

#### `TeamSpawned`

Fires after the team has fully spawned and roles are assigned.

* Use case: Give items, apply effects, or kill them >:)
* Arguments: `SummonedTeam`.

```cs
UCTEvents.TeamSpawned += OnTeamSpawned;

void OnTeamSpawned(TeamSpawnedEventArgs ev)
{
    foreach (var member in ev.SummonedTeam.Members)
    {
        member.Player.kill();
    }
}
```

#### `TeamEliminated`

Fires when the last member of a custom team dies.

* **Use case:** End the round, spawn a reinforcement wave, log stats, or announce the defeat.
* **Arguments:**
  * `SummonedTeam`: The team instance that was eliminated.
  * `TimeSurvived`: A `TimeSpan` indicating how long the team survived since spawning.

**Example:**

```csharp
UCTEvents.TeamEliminated += OnTeamEliminated;

void OnTeamEliminated(TeamEliminatedEventArgs ev)
{
    string duration = $"{ev.TimeSurvived.Minutes}m {ev.TimeSurvived.Seconds}s";
    
    Announcer.Message($"{ev.SummonedTeam.Definition.Name} eliminated after {duration}");
    Logger.Info($"Team {ev.SummonedTeam.Definition.Name} survived for {ev.TimeSurvived.TotalSeconds} seconds.");
}
```

