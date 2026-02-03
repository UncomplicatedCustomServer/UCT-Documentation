---
icon: trophy
---

# Win Condition

The Win Condition is a crucial component of UCT, enabling you to define the specific win criteria and faction alignment for a Custom Team. Additionally, it allows you to specify which base game Team serves as an ally.

## Win Condition

The **Win Condition** object should look like this:

```yml
   win_condition:
    prevent_round_end_if_alive: true
    allied_teams: []
    winning_team: Draw
```

## Prevent Round End If Alive

**Configuration element name:** `prevent_round_end_if_alive` \
**Type:**  `bool`

If true, the round will not end while this team is alive, effectively blocking standard round-end conditions.\
**NOTE:** This does **NOT** prevent the round from ending if this team wins by eliminating all enemies. If they win, the round ends immediately.

## Allied Teams

**Configuration element name:** `allied_teams` \
**Type: `List<Team>`**

A list of vanilla teams that are considered allies.\
The Custom Team does **NOT** need to eliminate players from these teams to trigger the win condition.

## Winning Team

**Configuration element name:** `winning_team` \
**Type: `LeadingTeam`**

The specific faction to declare as the winner when the win condition is met.
