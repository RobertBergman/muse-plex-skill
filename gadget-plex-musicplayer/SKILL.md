---
name: gadget-plex-musicplayer
description: Play music from the home Plex server by genre or album on the JBL Charge 4 Bluetooth speaker connected to this device, using the plexmusic command.
---

# Plex Music Player

Plays music from a Plex server on the JBL Charge 4 Bluetooth speaker attached to
this device. Run the commands below as the normal Muse command user (`muse`).

## Commands

All commands are `/opt/plexmusic/plexmusic <command>`:

| Command | Effect |
|---------|--------|
| `genres` | List genres in the Plex music library (one per line) |
| `play-genre <genre> [--no-shuffle]` | Play a genre, shuffled by default |
| `play-album <album> [--artist <artist>]` | Play an album in order |
| `now-playing` | Show the current track and its position in the queue |
| `playlist [--limit N]` | Show the upcoming queue (default 10) |
| `skip` | Next track; prints the new track |
| `stop` | Stop playback |

Examples:

```bash
/opt/plexmusic/plexmusic play-genre blues
/opt/plexmusic/plexmusic play-album "Led Zeppelin III" --artist "Led Zeppelin"
/opt/plexmusic/plexmusic skip
/opt/plexmusic/plexmusic stop
```

## How to use it

1. If the user names a genre you are unsure of, run `genres` first and use the exact name.
2. Start playback with `play-genre` or `play-album`. A new play command replaces whatever is playing.
3. Playback continues in the background after the command returns. Use `now-playing`, `skip` and `stop` to control it.
4. Each play command connects the speaker automatically if it is not connected.

## Limits

- Output is only the JBL Charge 4. If the speaker is off or out of range, play commands fail with
  "Speaker is not connected"; tell the user to turn it on and retry.
- No pause, volume or seek commands. Skip and stop only.
- Genre names must match the Plex library; matching is exact, so check `genres`.
- A genre play queues at most 500 tracks.
- Plex connection details are in `/home/muse/plex.env`, readable only by `muse`.
  Never print, log or share that file's contents. If Plex answers "401 Unauthorized",
  the token has expired and must be replaced by the device owner.

## Source

- `/opt/plexmusic/plexmusic` (Python 3, standard library only, plays through `mpv`)
- Skill format: https://github.com/facebookincubator/muse-gadget-sdk/tree/main/skills
