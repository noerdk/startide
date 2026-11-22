# FAQ and troubleshooting

[← Back to the README](../README.md)

- [What is Startide, exactly?](#what-is-startide-exactly)
- [It doesn't start](#it-doesnt-start)
- [There's no sound](#theres-no-sound)
- [Performance](#performance)
- [Using your own sounds](#using-your-own-sounds)
- [Wi-Fi MIDI](#wi-fi-midi)
- [Where things are kept](#where-things-are-kept)
- [Reporting a bug](#reporting-a-bug)

## What is Startide, exactly?

A generative ambient instrument. A piece is a key, a set of timbres and a pace, drawn from a
seed; the piece composes itself from there (drone, pads, bells, grains) and never repeats.
The knobs shape it, PLAY mode lets you play over it in key, and the AUTO DJ can run the whole
evening on its own.

## It doesn't start

Look at `App/Startide/log.txt` on the card. Its first lines show the screen, the input
devices and the sound setup Startide found.

- **The log is empty or missing:** Onion didn't run it. Check that the folder is
  `App/Startide` (not `App/Startide/Startide`) and that `launch.sh` is there.
- **The picture is upside down:** open `launch.sh` and set `SYNTH_ROTATE=0`.

## There's no sound

- Check the Miyoo's volume (Onion's own volume setting applies to Startide too).
- On Onion, Startide plays through Onion's audio server; if another app left it in a bad
  state, a restart of the Miyoo fixes it.
- The `audio:` line in `log.txt` shows what it found.

## Performance

Startide runs the CPU at full speed while it plays (it asks Onion's `cpuclock` for 1200 MHz).
`log.txt` has a status line every 10 seconds: *audio X% of its time budget* should stay
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

## Where things are kept

| What | Where on the card |
|---|---|
| Your session (knobs, piece, sound source, DJ) | `App/Startide/state.txt`, saved every 15 s and on quit |
| Save slots 1–4 | `App/Startide/saves/` |
| Recordings | `App/Startide/samples/REC 001.wav` … |
| The AUTO DJ's kept moments | `App/Startide/samples/DJ 001.wav` … `DJ 008.wav` |
| The log of the last run | `App/Startide/log.txt` |

## Reporting a bug

[Open an issue](https://github.com/noerdk/startide/issues/new/choose) and attach `log.txt`. Say
which device and firmware you use, and which version of Startide (it's in the release you
downloaded, and on the update screen).
