---
icon: screwdriver-wrench
---

# Developer's Dream

Welcome to the **UncomplicatedCustomTeams** API. We have completely refactored the internal structure to separate **Definitions** (Config) from **Runtime** (Live Game Objects). This makes it incredibly easy for external plugins to register custom teams, manipulate spawns, or listen to game events.

***

### 📦 Getting Started

To interact with the API, ensure you are using the correct namespaces:

```csharp
using UncomplicatedCustomTeams.API.Enums;
using UncomplicatedCustomTeams.API.Events;
using UncomplicatedCustomTeams.API.Features.Definitions; // For Config/Setup
using UncomplicatedCustomTeams.API.Features.Runtime;     // For Active Teams
using UncomplicatedCustomTeams.API.Features.Services;    // For Spawning Logic
```

