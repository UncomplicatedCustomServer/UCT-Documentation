---
icon: waveform-lines
---

# UCT Extensions

UCT integrates additional options into the configuration, allowing you to manage UCR roles more efficiently directly from the Custom Team Config.\
With this, you can (for example) set role priority, and UCT will spawn Custom Roles according to that priority (`First` = first, `Fifth` = last)."

## Sound Paths

The **Sound Paths** object should look like this:

```yml
  sound_paths:
  - path: /path/to/your/ogg/file
    delay: 0
```

## Path

**Configuration element name:** `path` \
**Type:**  `string`

The path to the `.ogg` sound file.\
Check [#sound-queue](uct-extensions.md#sound-queue "mention") for information on how to create a sound queue.

## Delay

**Configuration element name:** `delay` \
**Type:** `float`

Delay in seconds before sound starts playing.

## Sound Queue

To create a sound queue, you need to copy the entire Sound Paths content and paste it below. Like this:

```yml
  sound_paths:
  - path: /path/to/your/ogg/file1
    delay: 0
  - path: /path/to/your/ogg/file2
    delay: 0
  - path: /path/to/your/ogg/file3
    delay: 0
```
