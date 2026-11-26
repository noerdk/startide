# Installing Startide

[← Back to the README](../README.md)

## What you need

- A **Miyoo Mini** or **Mini Plus** running **[Onion OS](https://onionui.github.io/)** (4.x).
- Its SD card and a card reader for your computer.
- About **60 MB** free on the card (the app is ~3 MB; the rest is its sample library).

> **MinUI:** `Startide-MinUI.zip` is the same app packaged for MinUI. It hasn't been tried on
> a device yet; if you do, please [tell us how it went](https://github.com/noerdk/startide/issues/new/choose).

## Install on Onion OS

1. Download **`Startide-Onion.zip`** from the [latest release](https://github.com/noerdk/startide/releases/latest).
2. Put the SD card in your computer.
3. Unzip the file **to the root of the card**. It contains an `App` folder, which merges with
   the one already there, so you end up with:

   ```
   SD card
   └── App
       └── Startide
           ├── startide        the program
           ├── launch.sh       how Onion starts it
           ├── config.json     its entry in the Apps list
           ├── icon.png
           └── samples/        the sound library (add your own WAVs here)
   ```

4. Put the card back in the Miyoo and turn it on.
5. Open **Apps** → **Startide**.

The first start takes a second or two while the title fades in. Press **START** at any time
for the menu, or **START → HOW TO PLAY** for a tour of the buttons.

## Install on MinUI (untested)

1. Download **`Startide-MinUI.zip`** and unzip it to the root of the card. It adds
   `Tools/miyoomini/Startide mini.pak`.
2. Start it from **Tools**.

## Updating

From version 0.2 on, Startide updates itself over Wi-Fi: see [updating.md](updating.md).
To update by hand instead, unzip the new release over the old one. Your session, saves,
recordings and samples are kept: they're files the release doesn't contain.

## Uninstalling

Delete the `App/Startide` folder from the card. That removes everything, including your
recordings in `App/Startide/samples/`, so copy those first if you want to keep them.

## If it doesn't start

Startide keeps a log of each run in `App/Startide/logs/` (see the
[FAQ](faq.md#the-logs)). If you're stuck, attach both files to an
[issue](https://github.com/noerdk/startide/issues/new/choose).
