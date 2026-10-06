# Muse skill: Plex music player

A [Muse gadget skill](https://github.com/facebookincubator/muse-gadget-sdk/tree/main/skills) that plays music from a Plex server on a Bluetooth speaker attached to the Muse device.

- `gadget-plex-musicplayer/SKILL.md` - the skill (paste into your Muse chat, or give Muse a link to this repo).
- `plexmusic/plexmusic` - the command the skill calls. Python 3 standard library plus `mpv`; install at `/opt/plexmusic/plexmusic`.

## Setup on the device

1. Install `mpv` and pair the speaker with Bluetooth. Set `PLEXMUSIC_SPEAKER` or edit `SPEAKER_MAC` in the script.
2. Give the account Muse runs commands as (`MUSEGADGET_RUN_AS`) its own PulseAudio, and make that PulseAudio the owner of Bluetooth audio.
3. Create `/home/<that user>/plex.env` (mode 600) with `PLEX_URL` and `PLEX_TOKEN`. Do not commit it.
