---
icon: waveform-lines
---

# Sound Paths

Sound Paths in UCT define the audio playback triggered upon a Custom Team spawn. Since `sound_paths` is a list structure, you can duplicate objects within it to establish a playback queue.

**Note:** Audio playback requires [AudioPlayerApi](https://github.com/Killers0992/AudioPlayerApi) to be installed on the server. Please note that while this is no longer a hard requirement as of `v1.6.0`, AudioPlayer is still necessary on the server if you intend to use sound features.

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
Check [#sound-queue](sound-paths.md#sound-queue "mention") for information on how to create a sound queue.

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
