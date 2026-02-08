---
icon: calendar-days
---

# Events System

#### `TeamSpawning`

Fires before the team spawns.

* Use case: Cancel the spawn or modify the list of players.
* Arguments: `Team`, `PlayersToSpawn` (List\<Player>), `IsAllowed`.

C#

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

* Use case: Give custom items, apply effects, or send a broadcast.
* Arguments: `SummonedTeam`.

C#

```cs
UCTEvents.TeamSpawned += OnTeamSpawned;

void OnTeamSpawned(TeamSpawnedEventArgs ev)
{
    foreach (var member in ev.SummonedTeam.Members)
    {
        member.Player.SendBroadcast($"Welcome to {ev.SummonedTeam.Definition.Name}!", 5);
    }
}
```

#### `TeamEliminated`

Fires when the last member of a custom team dies.

* Use case: End the round, spawn a reinforcement wave, or announce the defeat.
* Arguments: `SummonedTeam`.

C#

```cs
UCTEvents.TeamEliminated += OnTeamEliminated;

void OnTeamEliminated(TeamEliminatedEventArgs ev)
{
    Announcer.Message($"{ev.SummonedTeam.Definition.Name} has been eliminated");
}
```

