# Using Santroller on Wii / Wii U

The Wii is an interesting case because different games use different types of instruments.

---

## Rock Band

Rock Band uses USB instruments. If you set your emulation mode to either `Rock Band Guitar` or `Rock Band Drums`, it will work out of the box.

---

## Guitar Hero / DJ Hero

Guitar Hero and DJ Hero instruments connect through the Wii Remote rather than USB. The legacy firmware cannot emulate a wired Wii Extension.

You must mod your Wii and use software to emulate a Wii Extension.

---

## Emulating a Wii Extension in software

A module is available that works with USB loaders and allows you to play Guitar Hero, Band Hero, and DJ Hero games using a USB instrument. This module is called **Santroller Brainslug**.

---

### Setting up Santroller Brainslug (Real Disc)

1. Download `sd.zip` from https://github.com/Santroller/santroller-bslug/releases/latest
2. Extract the contents to the root of your Wii SD card
3. Plug in the USB instrument
4. Launch the Homebrew Channel
5. Launch Brainslug

---

### Setting up Santroller Brainslug (USB Loader GX)

```danger
You need to be running the game from a USB disk!

Booting the game from the SD card locks the SD card, and because of that, brainslug isn't able to load the files it needs.
```


1. Download `sd.zip` from https://github.com/Santroller/santroller-bslug/releases/latest
2. Extract the contents to the root of your Wii SD card
3. Rename `RGHE52.dol` to the title ID of the game you want to play
   - You may copy and rename the file multiple times to support multiple games
4. Open USBLoaderGX
   - Other loaders may work, but instructions are only provided for USBLoaderGX
5. Open the loader settings for the game
6. Set `Game IOS` to `Custom`
7. Set `Custom Game IOS` to `249`
8. Set `Alternate dol` to `Load from SD/USB`
9. Save the settings
10. Plug in the USB instrument
11. Launch the game
