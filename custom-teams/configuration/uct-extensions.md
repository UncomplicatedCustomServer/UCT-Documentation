---
icon: circle-ellipsis
---

# UCT Extensions

UCT integrates additional options into the configuration, allowing you to manage UCR roles more efficiently directly from the Custom Team Config.\
With this, you can (for example) set role priority, and UCT will spawn Custom Roles according to that priority (`First` = first, `Fifth` = last)."

## Max Players

**Configuration element name:** `max_players`\
**Type:** `int32`

Specifies the maximum number of players that can spawn as this Custom Role.

## Priority

**Configuration element name:** `priority`\
**Type:**  [#priority](../../syntax/enums.md#priority "mention")

The priority of assigning Custom Role in the Spawn Wave (First -> Fifth).\
The lower the value, the higher the priority.

## Drop Inventory On Death

**Configuration element name:** `drop_inventory_on_death` \
**Type:** `bool`

Determines whether items are dropped upon the death of this specific Custom Role.

## Is Godmode Enabled

**Configuration element name:** `is_godmode_enabled` \
**Type:** `bool`\
\
<br>

Determines whether this Custom Role has God Mode enabled.

## Is Bypass Enabled

**Configuration element name:** `is_bypass_enabled` \
**Type:** `bool`\
\
<br>

Determines whether this Custom Role has Bypass enabled.

## Is Noclip Enabled

**Configuration element name:** `is_noclip_enabled` \
**Type:** `bool`\
\
<br>

Determines whether this Custom Role has Noclip enabled.
