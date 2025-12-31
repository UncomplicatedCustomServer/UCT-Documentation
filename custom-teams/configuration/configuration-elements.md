---
icon: ellipsis-vertical
---

# Configuration elements

Here the main configuration elements will be explained.\
You need to read the whole page in order to create basic Custom Roles with UCR.\
We'll always reference to the main YAML configuration given at the [Configuration](/broken/pages/upncLbsuFSs6OuLWKQuY) part of this wiki.

## Role ID

**Configuration element name:** `id` \
**Type:** `UInt32`

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

## Is Team Alive To Win Enabled

**Configuration element name:** `is_team_alive_to_win_enabled`\
**Type:** `bool`



## Health

The **Health** configuration parameter has its own object with its own specifications.\
Please visit [this page](/broken/pages/IuWRXpoRwDljOFO5k9eN#health) in order to read how to configure it.

## AHP

The **AHP** configuration parameter has its own object with its own specifications.\
Please visit [this page](/broken/pages/IuWRXpoRwDljOFO5k9eN#artificial-health-ahp) in order to read how to configure it.

## Hume Shield

The **Hume Shield** configuration parameter has its own object with its own specifications.\
Please visit [this page](/broken/pages/FNXdcV1mD1GjaIPFu8kY) in order to read how to configure it.

## Effects

The **Effects** configuration parameter has its own object with its own specifications.\
Please visit [this page](/broken/pages/OXlWFpRxrwEdSjDQImDI) in order to read how to configure it.

## Stamina

The **Stamina** configuration parameter has its own object with its own specifications.\
Please visit [this page](/broken/pages/JBOgvHEpLj0SSjpWCGCF) in order to read how to configure it.

## Max SCP-330 Candies

**Configuration element name:** `max_scp330_candies` \
**Type:** `int32`&#x20;

Indicates the maximum number of candies that can be taken from **SCP-330** without having your hands severed.

## Can Escape

**Configuration element name:** `can_escape` \
**Type:** `bool`&#x20;

Indicates whether the Custom Role can escape or not (through the exit on the Surface).\
The behavior behind the escape event is decided by editing the [Role After Escape](configuration-elements.md#role-after-escape) configuration parameter.

## Role After Escape

The **Role After Escape** configuration parameter has a complex syntax in order to allow server-owners to have a more advanced and complete configuration method to customize escape logic for each Custom Role.\
Please visit [this page](/broken/pages/usRBrqD8N1XxQLXSKycA) in order to learn the syntax and read how to correctly use it.

## Scale

**Configuration element name:** `scale` \
**Type:** `Vector3`&#x20;

A simple `Vector3` that decide the scale on the three dimensions (X, Y and Z).\
It's an object with three keys (x, y and z) and three `int32` as values.\
Example:

```yaml
scale:
  x: 1
  y: 2
  z: 1
```

## Spawn Broadcast

**Configuration element name:** `spawn_broadcast` \
**Type:** `string`&#x20;

The spawn broadcast that gets displayed to the user when they spawn as the Custom Role.\
Here you can use the Unity syntax to decide the text's size, color, weight and everything else.

You can choose the duration through the [Spawn Broadcast Duration](configuration-elements.md#spawn-broadcast-duration) configuration value.

## Spawn Broadcast Duration

**Configuration element name:** `spawn_broadcast_duration` \
**Type:** `ushort`&#x20;

The duration of the spawn broadcast in seconds.

## Spawn Hint

**Configuration element name:** `spawn_hint` \
**Type:** `string`&#x20;

The spawn hint that gets displayed to the user when they spawn as the Custom Role.\
Here you can use the Unity syntax to decide the text's size, color, weight and everything else.

You can choose the duration through the [Spawn Hint Duration](configuration-elements.md#spawn-hint-duration) configuration value.

## Spawn Hint Duration

**Configuration element name:** `spawn_hint_duration` \
**Type:** `float`&#x20;

The duration of the spawn hint in seconds.

## Custom Inventory Limits

**Configuration element name:** `custom_inventory_limits` \
**Type:** [`ItemCategory`](/broken/pages/qpXcToqiwmYjX74m5dCk#itemcategory), `sbyte`&#x20;

**This configuration value contains Enum values**: please visit the [Enums](/broken/pages/qpXcToqiwmYjX74m5dCk) page in order to learn more about them!

A simple Dictionary that allow server owners to edit the default inventory limits value for each Custom Role.\
For example Class-D have a limit of 3 firearms: with this configuration parameter you can increase or even decrease this value!\
**Note:** if an ItemCategory is not specified the plugin will use it's default value!

Example:

```yaml
custom_inventory_limits:
  Firearm: 1
  Grenade: 5
```

_(Yeah now you can have up to 5 grenades but only 1 firearm)_

## Inventory

**Configuration element name:** `inventory` \
**Type:** [`[]ItemTypeId`](/broken/pages/qpXcToqiwmYjX74m5dCk#itemtype)&#x20;

**This configuration value contains Enum values**: please visit the [Enums](/broken/pages/qpXcToqiwmYjX74m5dCk) page in order to learn more about them!

Customizing the inventory of a Custom Role might be the most important thing to do and UCR gives you a simple -but powerful- tool to achieve that.\
The **Inventory** configuration value is a simple list of ItemTypes: every item will be added to the player's inventory.

Example:

```yaml
inventory:
- Flashlight
- KeycardJanitor
```

## Custom Items Inventory

**Configuration element name:** `custom_items_inventory` \
**Type:** `[]int32`&#x20;

UCR does support both **EXILED CustomItems** and **UncomplicatedCustomItems** (UCI) and with this configuration parameter you can add Custom Items from both plugins to your Custom Role.\
Just put the Custom Item's Id and it will be given!\
**Note:** remember to NOT have Id conflicts between EXILED CI and UCI as if you have two items with the same Id UCR will always take the UCI one!

Example:

```yaml
custom_items_inventory:
- 2
- 5
```

## Ammo

**Configuration element name:** `ammo` \
**Type:** [`[]AmmoType`](/broken/pages/qpXcToqiwmYjX74m5dCk#ammotype)

**This configuration value contains Enum values**: please visit the [Enums](/broken/pages/qpXcToqiwmYjX74m5dCk) page in order to learn more about them!

You can also customize the amount of ammo that a Custom Roles has.\
**Note:** the plugin actually overrides the default amount of ammo: for that reason if you don't give ammo to a Custom Role it won't have **any** of them!

## Damage Multiplier

**Configuration element name:** `damage_multiplier` \
**Type:** `float`&#x20;

The damage multiplier that will be applied to the damage dealt by **this role** to another player.\
We use the following formula:

```
newDamage = oldDamage * damage_multiplier
```

For that reason if the value is `1` then nothing will change while if we set the value for example to `1.5` and we deal `20HP` the given damage will be `30HP`.

## Spawn Settings

The **SpawnSettings** configuration parameter has its own object as it's a main part of the configuration and because of its complexity another page is needed for a better organization.\
Please visit this page in order to read more about the Spawn Settings param.

## Custom Flags

With the `v6.0.0` **Custom Flags** officially became open to the developers and because of that the system changed in a more customizable -but complex- one.\
The explanation (with the list of built-in Custom Flags) is available at [this page](/broken/pages/JUs0UnspqIL28yUc0BOM).

## Ignore Spawn System

**Configuration element name:** `ignore_spawn_system` \
**Type:** `bool`&#x20;

If true the Custom Role won't be evaluated by our Spawn System but you'll be able to spawn it manually using commands!
