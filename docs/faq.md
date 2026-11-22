# FAQ and troubleshooting

[← Back to the README](../README.md)

- [What is Startide, exactly?](#what-is-startide-exactly)
- [It doesn't start](#it-doesnt-start)
- [There's no sound](#theres-no-sound)
- [Performance](#performance)
- [Using your own sounds](#using-your-own-sounds)
- [Wi-Fi MIDI](#wi-fi-midi)
- [The logs](#the-logs)
- [Where things are kept](#where-things-are-kept)
- [Reporting a bug](#reporting-a-bug)

## What is Startide, exactly?

A generative ambient instrument. A piece is a key, a set of timbres and a pace, drawn from a
seed; the piece composes itself from there (drone, pads, bells, grains) and never repeats.
The knobs shape it, PLAY mode lets you play over it in key, and the AUTO DJ can run the whole
evening on its own.

## It doesn't start

Look at `App/Startide/logs/current.txt` on the card (see [the logs](#the-logs)). It shows
the screen, the input devices and the sound setup Startide found.

- **The log is empty or missing:** Onion didn't run it. Check that the folder is
  `App/Startide` (not `App/Startide/Startide`) and that `launch.sh` is there.
- **The picture is upside down:** open `launch.sh` and set `SYNTH_ROTATE=0`.

## There's no sound

- Check the Miyoo's volume (Onion's own volume setting applies to Startide too).
- On Onion, Startide plays through Onion's audio server; if another app left it in a bad
  state, a restart of the Miyoo fixes it.
- The `audio:` line in `logs/current.txt` shows what it found.
- If the sound stops in the middle of playing, Startide says so on screen; the log has a
  CRASH block saying why. Starting it again brings the sound back.

## Performance

Startide runs the CPU at full speed while it plays (it asks Onion's `cpuclock` for 1200 MHz).
The log has a status line every 10 seconds for the first minute, then every minute:
*audio X% of its time budget* should stay
well under 100% (it's around 35–45% on a Mini Plus).

If the sound crackles, open `launch.sh`:
- `SYNTH_SR=32000` is the engine's own rate (the Miyoo always gets 48 kHz, converted inside
  Startide). 24000 eases it further; 48000 adds the last bit of air.
- `SYNTH_FPS=24` is the screen's frame rate; 20 frees a little more time.

## Using your own sounds

Put **WAV** files (8, 16, 24 or 32-bit, or 32-bit float; mono or stereo; any sample rate) in `App/Startide/samples/`.
Pick one with the **SOURCE** knob (Grain Storm, bank B). About 10–30 seconds without gaps
works best.

Grains are tuned into the music's key. If you know a file's key, add a line to
`samples/keys.txt`:

```
MY PAD=D MINOR
RAIN NOISE=NONE
```

(`NONE` for sounds without a pitch.) Files not listed are analysed the first time you
choose them.

## Wi-Fi MIDI

**START → CONNECT → WIFI MIDI** makes Startide a network MIDI device (RTP-MIDI): on a Mac it
shows up in *Audio MIDI Setup → MIDI Studio → Network* as "Startide"; on Windows use rtpMIDI.
Notes play at their own pitch; **AUTOPLAY** decides whether the piece keeps playing itself
while you do, and **FIT TO KEY** moves every note into the current key.

## The logs

Startide keeps a log of each run in `App/Startide/logs/`:

| File | What's in it |
|---|---|
| `current.txt` | the last (or current) time Startide ran |
| `previous.txt` | the time before that |

Each log starts with the Startide version, firmware, device and settings, and says how the
run before it ended: **ended normally**, **CRASHED**, or **stopped without quitting** (the
battery ran out, the power button, or a crash). Then comes a timeline of what was done (menu
choices, page changes, sound sources, updates) and, if Startide crashed, a **CRASH** block
saying where.

If something goes wrong and you start Startide again to check, the evidence moves to
`previous.txt`, so attach **both** files to a bug report. They never grow large: a long run
is trimmed to its beginning and its last minutes, so together they stay under half a megabyte.

## Where things are kept

| What | Where on the card |
|---|---|
| Your session (knobs, piece, sound source, DJ) | `App/Startide/state.txt`, saved every 15 s and on quit |
| Save slots 1–4 | `App/Startide/saves/` |
| Recordings | `App/Startide/samples/REC 001.wav` … |
| The AUTO DJ's kept moments | `App/Startide/samples/DJ 001.wav` … `DJ 008.wav` |
| The logs of the last two runs | `App/Startide/logs/` |

## Reporting a bug

[Open an issue](https://github.com/noerdk/startide/issues/new/choose) and attach the two files
from `App/Startide/logs/`. They already say which version, firmware and device you have.
