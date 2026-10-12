---
layout: default
---

![Santroller](assets/images/logo.png)

The Santroller legacy platform programs AVR microcontrollers to emulate rhythm game controllers on computers and supported consoles.

> **This legacy firmware and configurator is no longer supported or maintained.** For the currently supported Santroller tooling, visit [santroller.com](https://santroller.com). If you are using a Raspberry Pi Pico, go to [santroller.com](https://santroller.com) for the supported tooling; this legacy release does not support Pico boards.

# Gallery

[![home screen](assets/images/screenshots/home.png)](assets/images/screenshots/home.png)
[![main screen](assets/images/screenshots/main.png)](assets/images/screenshots/main.png)
[![main screen with everything](assets/images/screenshots/combined.png)](assets/images/screenshots/combined.png)
[![adaptor](assets/images/adaptor.jpg)](assets/images/adaptor.jpg)
[![PS2 adaptor](assets/images/adaptor-ps2.jpg)](assets/images/adaptor-ps2.jpg)
[![directly wired controller](assets/images/direct.jpg)](assets/images/direct.jpg)
[![inline LEDs](assets/images/inline-led.jpg)](assets/images/inline-led.jpg)

# Supported microcontrollers

{% include sections/microcontrollers.md %}

# Features

- Directly wired guitar, drum, turntable, gamepad, keyboard, and stage-kit controllers
- Wii Extension and PS2 controller input adapters
- Guitar Hero neck, slider, turntable platter, MPR121, and accelerometer inputs
- Digital, analog, multiplexer, shortcut, and constant inputs
- Guitar Hero, Rock Band, DJ Hero, standard gamepad, keyboard, and Fortnite Festival output modes
- Automatic console detection and configurable mode bindings
- XInput and HID modes on Windows
- Configuration presets that can be exported and imported
- APA102-compatible RGB LEDs, standard LEDs, MPR121 GPIO LEDs, and STP16CPC26 LED drivers
- Player LEDs, rumble, stage-kit outputs, and supported game-event LED bindings

This legacy AVR firmware does not support Raspberry Pi Pico boards, USB Host inputs or authentication passthrough, Bluetooth, peripheral controllers, USB or serial MIDI inputs, WS2812 LEDs, Wii Extension output, or PS2 controller output. It is provided as an archived release and is not receiving updates or support.

```note
Avoid USB 2.0 hubs when using these controllers. Their high polling rate can slow down multiple controllers on one hub and may cause detection issues. USB 3.0 hubs are recommended.
```

# How to build an adaptor or controller

Pick a guide from the navigation to learn how to build a supported controller or adaptor.

# Need help?

[Join the Discord](http://discord.gg/CmdYpXKcEU) for help.

# Download

[Download the archived Santroller Legacy v10.1.189-legacy.2 release](https://github.com/Santroller/Santroller/releases/tag/v10.1.189-legacy.2). For the currently supported tooling, visit [santroller.com](https://santroller.com).

# Donate

I have put several years of development time into this project. If you like it, feel free to support the project:

{% include sponser.html %}

# Current sponsors

<div class="sponsors">
<!-- sponsors --><!-- sponsors -->
</div>
