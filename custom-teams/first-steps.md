---
description: >-
  With UCT you can create Custom Teams for your EXILED server. But what's a
  Custom Team?
icon: map-pin
---

# First steps

## What's a Custom Team?

Custom Team defines a unit consisting of Custom Roles, designed to replicate teams such as the Nine-Tailed Fox or Chaos Insurgency. The plugin supports extensive configuration through easy-to-manage `YML` files.

UCT is compatible with UCR (UncomplicatedCustomRoles); this integration allows roles defined in either UCR or UCT to spawn during a Custom Team spawn wave.

## Why mention roles from UCT or UCR?

Since UCT utilizes UCR to register Custom Roles internally, UCT Roles and UCR Roles **must not share the same ID.**

Additionally, UCT fully supports EXILED Custom Roles. You can spawn these roles within a Custom Team simply by inputting the corresponding EXILED Custom Role ID.

### Folder structure

UCT maintains a straightforward directory structure.

Located at `EXILED/Configs/UncomplicatedCustomTeams/{your-server-port}`, you will find `example-team.yml`, which contains the default Custom Team config.

To create new team files in the port folder, you can:

* Manually: Copy and paste existing files.
* Automatically: Run the command `uct generate <name>`.
