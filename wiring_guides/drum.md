---
sort: 3
---

# Setting up a Drum Kit


```danger
   If you have a GHWT or Band Hero Drum kit, you do NOT need to go down this method of hardwiring. The GHWT drum kits can be hardwired by connecting the microcontroller to the connector going to the brain, as there are just digital signals there and Santroller supports those signals.

   Band Hero drum kits are modded a bit differently. If you open up the brain, you can remove the PCB with the microcontroller on it from the main PCB, then solder the replacement microcontroller to the I2C lines and the buttons directly to the microcontroller.
   I have not written documentation for either of these methods yet, but feel free to join the discord and ask for help, we can run you through how to do this there.
```

## Supplies

- A microcontroller

  {% include sections/microcontrollers.md %}

- An optional 4051 or 4067 based analog multiplexer if the microcontroller does not have enough analog inputs
  - 74HC4051 / 74HC4067 parts are recommended, as they switch faster than CD4051B/CD4067B parts.
  - The CD4051B/CD4051BE and CD4067B aren't recommended as they are slower parts
    - However if you do get one of these, make sure to go for the slow multiplexer option when configuring, otherwise you will end up with drums reading inputs across multiple channels.

- 3.3V zener diode per drum / cymbal pad (if using a multiplexer)
  - The multiplexers do not like high voltage spikes, and the zener diode will clamp them. Without this, you will get very messy readings when a drum is hit.

- 1MOhm resistor per drum / cymbal pad
- Some Wire
- Soldering Iron
- Multimeter (it will be used mainly in continuity mode, where it beeps when the two contacts are shorted together)
- Wire Strippers
- Wire Cutters
- Heatshrink

- Supplies for specific features
  - Drum kit from scratch
    - 1 Piezo sensor per drum pad / cymbal

```note
Close the tool if you want to use your drum kit, the multiplexer is overridden by the tool when it updates its sensor values, and this will override the controller inputs when it happens.
```

## Wiring Steps

{% include sections/getting_started.md %}

To keep the relevant information in this guide easy to find, information is sorted by function.

<details>
    <summary>Face buttons</summary>

1. Trace the pads on the drum PCB that contains the face buttons. The face buttons should have a common ground, you should see this as a trace that connects multiple buttons together. Find some way to connect a wire to this, if there is a test pad or something you can solder to, solder your wire to that, otherwise you will need to scrape back one of the traces with a knife so you can solder to that. Solder this to ground on your microcontroller.
2. Follow the traces for the other side of each button, and solder a wire to them in a similar way as the common wire. Then solder that to a digital pin on your microcontroller.

</details>

<details>
    <summary>Multiplexer</summary>

[![4051](/assets/images/cd4051.png)](/assets/images/cd4051.png)
[![4067](/assets/images/cd4067.png)](/assets/images/cd4067.png)

1. Wire V<sub>CC</sub> on the multiplexer to V<sub>CC</sub> on the microcontroller.
2. Wire V<sub>SS</sub> to GND on the microcontroller.
3. If your multiplexer has a V<sub>EE</sub>, also wire that to ground. V<sub>EE</sub> allows for using the multiplexer with negative voltages, but since we aren't doing this we set it to ground to disable that feature.
4. Also wire INH / Inhibit to ground, if this exists on your multiplexer. This pin disables the I/O if it is driven high, so we ground it to make sure the chip is always enabled.
5. Wire the analog output (often labelled COM, common in/out, or SIG) on the multiplexer to an analog pin on your microcontroller.
6. Wire A/S0, B/S1 and C/S2 (and D/S3 for the 16 channel multiplexer) to separate digital pins on your microcontroller.
7. Wire each drum pad to a different channel on the multiplexer.

</details>

<details>
    <summary>Drum / Cymbal pads</summary>

```danger
   Note that the piezo is directional and does need to be wired in the correct way. If it doesn't work, swap the wires around.
```
1. Disconnect the piezos from the main drum PCB.
2. Solder the black wire from the piezo to ground.
3. Solder the red wire to an analog input on the multiplexer / micocontroller.
4. Solder a 1Mohm resistor between the analog input your piezo is connected to on your multiplexer / microcontroller and ground
5. Solder a diode between the analog input your piezo is connected to on your multiplexer / microcontroller and ground

</details>

<details>
    <summary>RB Pedal</summary>

1. The pedal connector has two wires coming out of it. Connect one to ground and one to a digital pin on your microcontroller.

</details>

<details>
    <summary>GH Pedal</summary>

1. Solder the one wire from the pedal connector to ground.
2. Solder the other wire to an analog input on the multiplexer, or directly to an analog pin on your microcontroller if it has enough analog pins.
3. Solder a 1Mohm resistor between the two wires on the pedal connector.

</details>

## Programming

1.  Start Santroller with your microcontroller plugged in.
2.  Set the Input Type to Directly Wired
3.  Click on `Configure`
4.  Click on `Controller Settings`
5.  Set `Emulation Type` to `Controller` for standard guitars and `Fortnite Festival` for Fortnite Festival.
6.  Set the `Controller Type` based on the game you want to play.
7.  `Windows controller mode` can be set based on your preferences. Note that this is only for Windows, no other operating systems or consoles will be affected by this option.
    1. `XInput` - This works more natively on windows, and most games will automatically bind controls.
    2. `HID` - This uses HID on windows, which means games won't automatically bind controls, but HID is polled a bit more efficiently in games like Clone Hero.
8.  If you would like to adjust settings related to polling, click on `Controller Poll Settings`
9.  Set the Poll Rate to your preferred setting. 0 sends data as fast as possible, any other number polls inputs at that speed.
10. Debounce can be adjusted here. You will need to increase this, as debounce sets the minimum time for a drum hit, and this will turn the drum hit that only occurs for a few microseconds into a signal that the game expects. While testing I used a debounce of 20ms but you will have to adjust this to find a value that works for you. The main thing to consider is that it takes a bit of time between you going to hit a drum pad and you hitting the pad, so if the debounce is too low, you may just miss drum hits due to the note not being on for long enough.
11. Now you can start setting up your inputs. To keep this information relevant, it is grouped by function.
    <details>
      <summary>Face buttons / RB Pedal</summary>

    1. Click on the button you want to configure, and make sure the `Input Type` is set to `Digital Pin Input`.
    2. Make sure `Pin Mode` is set to `Pull Up`.
    3. Click on the `Find Pin` button, and then press the button on the guitar. If you have wired everything correctly, the tool should detect the pin and the icon for that button should now light up whenever the button is pressed.

    </details>

    <details>
      <summary>Drum / Cymbal pads / GH Pedal (Multiplexer)</summary>

    4. Click on the drum pad in question
    5. Set the `Input Type` to multiplexer
    6. Set the S0, S1, S2 (and S3 for a 4067 based multiplexer) pins
    7. Set the analog output / SIG / COM pin to the analog pin you wired it to
    8. Hit the drum pad in question. You should see the raw value for the drum pad change.
    9. Hit the pad lightly, and drag the minimum up so that it registers small hits.
    10. Hit nearby pads and make sure that the vibrations from those pads don't activate the pad you are configuring. If they do, then increase the minimum. You should end up with each pad registering hits, without crosstalk or needing to hit the pads too hard.

    </details>

    <details>
      <summary>Drum / Cymbal pads / GH Pedal (Direct analog)</summary>

    11. Click on the drum pad in question
    12. Set the `input type` to `Analog Pin Input`
    13. Click on `Find Pin` and then hit the drum pad in question, it should detect the drum that was just hit.
    14. Hit the drum pad in question. You should see the raw value for the drum pad change.
    15. Hit the pad lightly, and drag the minimum up so that it registers small hits.
    16. Hit nearby pads and make sure that the vibrations from those pads don't activate the pad you are configuring. If they do, then increase the minimum. You should end up with each pad registering hits, without crosstalk or needing to hit the pads too hard.

    </details>
