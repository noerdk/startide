# Updating

[← Back to the README](../README.md)

Startide updates itself over Wi-Fi from this repository's
[releases](https://github.com/noerdk/startide/releases).

## How it works

1. **It looks.** A few seconds after Startide starts, if the Miyoo is on Wi-Fi, it asks
   GitHub whether there's a newer release. This happens in the background and doesn't
   affect the sound. With no Wi-Fi, it simply doesn't find anything.
2. **It tells you.** If a newer version is out, a line says so for a few seconds, and the
   Start menu gets an **UPDATE TO x.y.z** line under NEW PIECE.
3. **You choose.** Nothing changes until you pick that line and press **A**. The update
   screen shows the version and what's new; **B** closes it for now.
4. **It installs safely.** Every file is downloaded next to the old one and checked
   against its SHA-256 fingerprint from the release. Only when all of them are complete
   and correct are they swapped in. A dropped connection or a damaged download changes
   nothing, and **A** tries again.
5. **It restarts** into the new version, right where you were.

Your session, saves, recordings and samples are never touched by an update.

> **Original Miyoo Mini:** it has no Wi-Fi, so it never finds an update by itself. Download
> the new `Startide-Onion.zip` and unzip it over the old copy on the SD card; your session,
> saves and samples stay as they are.

## Turning Wi-Fi on

On Onion: **Settings → Network → Wi-Fi**. Startide checks once per start, so start it
again after connecting.

## If it never offers an update

- **Check the date and time** (Onion: *Settings → Time*, or *Tweaks → System → Clock*). Secure
  connections need the clock to be roughly right; the log says so if this is the problem.
- `App/Startide/logs/current.txt` has an `update:` line on every start that says what it found.

## Updating by hand

Download the zip from the [latest release](https://github.com/noerdk/startide/releases/latest)
and unzip it over the old copy, as in [the install guide](install.md).

## What an update contains

Each release carries a small manifest per platform (`manifest-miyoo.txt`): the version, one
line about what's new, and the size and SHA-256 of each file. The files are attached to the
release next to it. Updates replace only the program; your launcher and settings files stay.
