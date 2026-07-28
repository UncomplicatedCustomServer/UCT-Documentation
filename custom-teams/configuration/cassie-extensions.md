---
icon: volume-high
---

# Cassie Extensions

An extension for Cassie that introduces dynamic variables Cassie is able to read and announce. You can insert them directly into your custom Cassie messages and their corresponding translations. The plugin will automatically parse and replace these placeholders with live game data when the announcement plays.

## Available Variables

* **`{SCPLEFT}`** Returns the exact number of currently living SCP subjects.
* **`{MTFLEFT}`** Returns the total number of alive players belonging to the Foundation Forces (Mobile Task Force and Facility Guards).
* **`{CHAOSLEFT}`** Returns the total number of alive players on the Chaos Insurgency team.
* **`{CLASSDLEFT}`** Returns the number of currently living Class-D personnel.
* **`{SCIENTISTLEFT}`** Returns the number of currently living Scientists.
* **`{ROUNDTIME}`** Returns the total elapsed time of the current round. This variable is automatically formatted into spoken English, adjusting dynamically for singular and plural words (for example: "1 minute and 30 seconds" or "45 seconds").

**Example Usage**

**Message configuration:**

```yaml
cassie_message: "ATTENTION ALL PERSONNEL . {SCPLEFT} SCP ALIVE . TIME {ROUNDTIME}"
cassie_translation: "Attention all personnel. {SCPLEFT} SCP subjects remain. Time elapsed: {ROUNDTIME}."
```

