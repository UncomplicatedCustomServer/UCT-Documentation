---
icon: gear-complex
---

# Configuration elements

Here the main configuration elements will be explained.\
You need to read the whole page in order to create basic Custom Roles with UCR.\
We'll always reference to the main YAML configuration given at the [Configuration](/broken/pages/upncLbsuFSs6OuLWKQuY) part of this wiki.

## Role ID

**Configuration element name:** `id` \
**Type:** `uint32`

The unique Identifier for your Custom Team.\
You'll have to use this in order to spawn a players as that Custom Team and to get information about that Custom Team.\
Identifiers **must** be unique so watch out to avoid using the same Id for multiple Teams: only the first one will be loaded!

## Team Name

**Configuration element name:** `name` \
**Type:** `string`&#x20;

The name of the Custom Team.\
This is displayed when using the `uct list` command.

## Min Players

**Configuration element name:** `min_players`\
**Type:** `int32`

The minimum number of players that are required to be on the server to make this Custom Team spawn.

## Max Spawns

**Configuration element name:** `max_spawns`\
**Type:** `int32`

The maximum number of times this team can be spawned in a single round. Set to -1 for unlimited.

## Spawn Chance

**Configuration element name:** `spawn_chance` \
**Type:** `uint32`

The chance of spawning of this Custom Team.&#x20;0 is 0% and 100 is 100%.

## Allow Concurrent Spawns

**Configuration element name:**  `allow_concurrent_spawns`\
**Type:** `bool`

If set to true, this Custom Team's successful spawn roll will not prevent other Custom Teams with the same SpawnWave from being evaluated.

## Spawn Condition

The **Spawn Condition** configuration parameter has its own object with its own specifications.\
Please visit [this page](spawn-condition.md) in order to read how to configure it.

## Is Cassie Announcement Enabled

**Configuration element name:** `is_cassie_annoucement_enabled` \
**Type:** `bool`&#x20;

Should the Cassie Announcement be enabled? If yes, the Cassie Message **must also be provided!**

## Cassie Message

**Configuration element name:** `cassie_message` \
**Type:** `string`

The message that will be spoken by CASSIE after this Custom Team spawns.

## Cassie Translation

**Configuration element name:** `cassie_translation` \
**Type:** `string`

The translation of the message spoken by CASSIE.

## Is Noisy

**Configuration element name:** `is_noisy`\
**Type:** `bool`

Should the announcement sound play before the CASSIE message? If false, only the message itself will be sent without the sound.

## Win Condition

The **Win Condition** configuration parameter has its own object with its own specifications.\
Please visit [this page](win-condition.md) in order to read how to configure it.

## Sound Paths

The **Sound Paths** configuration parameter has its own object with its own specifications.\
Please visit [this page ](sound-paths.md)in order to read how to configure it.

## Sound Volume

**Configuration element name:** `sound_volume` \
**Type:** `float`

Volume of played audio files.\
**VERY VERY IMPORTANT: IF YOU ARE UNSURE IF A VALUE OF 1 IS SUFFICIENT, 99% OF THE TIME IT IS. INCREASING IT MAY CAUSE EARRAPE!!**



## UCR SECTION

The UCR configuration section is located below within the Custom Team Config. For configuration instructions, please refer to the [UCR Wiki](https://app.gitbook.com/o/GOLA1dHs7HSH2zbizA76/s/7dNIcOcinWdoZSPkGHCX/).

UCT injects additional options into the UCR Config; to view these specific settings, check here.
