---
sort: 4
---

# Setting up a Turntable

## Wiring

### Supplies

- A microcontroller

  {% include sections/microcontrollers.md %}

- Some Wire
- Soldering Iron
- Multimeter (it will be used mainly in continuity mode, where it beeps when the two contacts are shorted together)
- Wire Strippers
- Wire Cutters
- Heatshrink

### Wiring Steps

{% include sections/getting_started.md %}

To keep the relevant information in this guide easy to find, information is sorted by function.

<details>
    <summary>Effects Knob</summary>

1. Wire one of the outer pins to V<sub>CC</sub>
2. Wire the other outer pin to GND
3. Wire the middle pin to an analog pin on your microcontroller.
</details>

<details>
    <summary>Crossfader</summary>

1. Follow the pins going to the Crossfader. There should be three pins.
2. Wire one of the outer pins to V<sub>CC</sub>
3. Wire the other outer pin to GND
4. Wire the middle pin to an analog pin on your microcontroller.
</details>

<details>
   <summary>Euphoria Button and LED</summary>

1.  Connect V to V<sub>CC</sub> on your microcontroller.
2.  Connect V0 to ground on your microcontroller.
3.  Connect AT to one of the following pins

    | Microcontroller            | PWM Pins     |
    | -------------------------- | ---------------------- |
    | Pro Micro, Leonardo, Micro | 3, 5, 6, 9, 10, 11, 13 |
    | Uno                        | 3, 5, 6, 9, 10         |
    | Mega                       | 2 - 13, 44 - 46        |

</details>

<details>
    <summary>Face buttons</summary>

1. Remove the face button PCB from the turntable
2. There is a smaller PCB attached to the main button PCB with headers, which contains the main micro controller. Disconnect this in some way, either by cutting it away, desoldering it or cutting traces going to the microcontroller on it. Be careful though, as the traces on these PCBs are very cheap and can break very very easily.
3. Follow the traces from each pad. You will find that there will be common traces going to multiple pads, which you can connect to ground. Connect the other trace going to each pad to a digital pin on your microcontroller. In effect, you should end up with one side of every pad going to ground, and the other side going to a digital pin. Some tables may even have the pins labeled for you, which can make things easier.
</details>

<details>
    <summary>Platter (Standard)</summary>

1.  The platters connect to the same PCB that the crossfader is on. There will be some labelled pads, V, C, D and G.
2.  Hook up V to V<sub>CC</sub> and G to GND. For safety I would recommend hooking V to 3.3v on a 5v microcontroller, as most I2C devices I have come across don't like being powered by 5v.
3.  Hook up C to SCL and D to SDA using the pins below.

| Microcontroller            | SDA (D) | SCL (C) |
| -------------------------- | ------- | ------- |
| Pro Micro, Leonardo, Micro | 2       | 3       |
| Uno                        | A4      | A5      |
| Mega                       | 20      | 21      |

</details>

## Programming

1.  Start Santroller with your microcontroller plugged in.
2.  Set the Input Type to Directly Wired
3.  Hit Configure
4.  Click on `Controller Settings`
5.  Set `Emulation Type` to `Controller`
6.  Set the `Controller Type` to `DJ Hero Turntable`.
7.  `Windows controller mode` can be set based on your preferences. Note that this only affects windows, a controller in XInput mode will use the correct mode on a console, and will automatically use HID mode on Linux and macOS.
    1. `XInput` - This works more natively on windows, and most games will automatically bind controls.
    2. `HID` - This uses HID on windows, which means games won't automatically bind controls, but HID is polled a bit more efficiently in games like Clone Hero.
8.  If you would like to adjust settings related to polling, click on `Controller Poll Settings`
9.  If you would like to use `Queue Based Inputs` you can turn that on here. This puts any buttons you press into a queue, and sends them out to the PC as fast as USB allows. This means that the controller will process your inputs at a faster poll rate than 1ms (the fastest rate USB allows) and then the PC will be sent your inputs at a 1ms rate.
10. Set the Poll Rate to your preferred setting. 0 sends data as fast as possible, any other number polls inputs at that speed.
11. Debounce can be adjusted here. Debounce is necessary as button inputs are noisy. When you hit a button, it will often bounce and send multiple presses, which some games may percieve as you hitting the button multiple times, which can result in dropped sustains. When you set debounce to a value, the signal ignores any release inputs for that time frame, so if you for example set it to 1ms, then the button input will be on for a minimum of 1ms, and only after that will the release be processed. This has the effect of stretching out the button press to at least 1ms, which ignores any bouncing in that timeframe.
12. Now you can start setting up your inputs. To keep this information relevant, it is grouped by function.
    <details>
      <summary>The Platter</summary>

    1. Click on `Dj Turntable Inputs`.
    2. Set the SCL and SDA pins that you have wired the platter to.
    3. Leave the turntable poll rate at 10ms. If you poll it any quicker than this, the platter velocity will be less accurate due to how it is polled.

    </details>
    <details>
      <summary>Buttons or Dpad</summary>

    1. Click on the button you want to configure, and make sure the `Input Type` is set to `Digital Pin Input`.
    2. Make sure `Pin Mode` is set to `Pull Up`.
    2. Click on the `Find Pin` button, and then press the button on the guitar. If you have wired everything correctly, the tool should detect the pin and the icon for that button should now light up whenever the button is pressed.

    </details>

    <details>
      <summary>Joystick</summary>

    1. Click on D-pad Left, and set the `Input Type` to `Analog Pin Input`.
    2. Set `Type` to `Joystick Negative`
    3. Click on find pin and move the joystick left or right
    4. Adjust the threshold so that the D-pad Left icon lights up when you have pushed the Joystick far enough to the left. This means you can adjust how sensitive you want your joystick to be.
    5. You can do the same for D-pad right, however, set the `Type` to `Joystick Positive` instead.
    6. If you wish to also map joystick up and down, click `Add Setting` and add another Strup Up and Strum Down input. Then you can follow the above instructions again, only using negative for up and positive for down, and when detecting the pin, move the joystick up and down instead.

    </details>

    <details>
      <summary>Crossfader</summary>

    1. Click on the crossfader, and make sure the `Input Type` is set to `Analog Pin Input`.
    2. Click on the `Find Pin` button, and then press on the whammy. If you have wired everything correctly, the tool should detect the pin and the `Original Value` value should change when you push on the whammy.
    3. Click on `Calibrate`.
    4. Move the crossfader all the way left and hit `Next`.
    5. Move the crossfader all the way right, and hit `Next`
    6. Move the crossfader to the center, and hit `Next`.
    </details>

    <details>
      <summary>Effects Knob</summary>

    1. Click on the Effects Knob, and make sure the `Input Type` is set to `Analog Pin Input`.
    2. Click on the `Find Pin` button, and then press on the whammy. If you have wired everything correctly, the tool should detect the pin and the `Original Value` value should change when you rotate the effects knob.
    </details>

13. If you do not want to hook an input up, hit the `Remove` button to the right on that input.
14. Once everything is configured correctly, the `Save Settings` button should be clickable and you can hit that button to write your config to the guitar. It is now ready.
