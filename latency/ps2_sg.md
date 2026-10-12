---
sort: 10
---

# PS2 SG

Latency of an input from a PS2 Wired SG Guitar.

Measured by connecting it to the microcontroller in question, and then sending a signal to toggle the strum up input, and timing how long it takes that signal to reach a target device over USB.
Note that the console only polls this controller every 10ms or so. The developers of the controller took this into account, and the controller will lock up if it is polled too quickly.

| microcontroller | Sparkfun Pro Micro 5V | Sparkfun Pro Micro 3.3V | Arduino Uno |
| :-------------- | :-------------------- | :---------------------- | :---------- |
| controller      | PS2 SG                | PS2 SG                  | PS2 SG      |
| poll rate       | 1 ms                  | 1 ms                    | 1 ms        |
| min             | 4.02 ms               | 4.14 ms                 | 6.04 ms     |
| max             | 12.36 ms              | 10.84 ms                | 12.96 ms    |
| avg             | 7.68 ms               | 7.39 ms                 | 9.66 ms     |
| stddev          | 1.8 ms                | 1.69 ms                 | 1.77 ms     |
| %on time        | 54%                   | 56%                     | 42%         |
| %1f skip        | 46%                   | 44%                     | 58%         |
| %2f skip        | 0%                    | 0%                      | 0%          |
| %3f skip        | 0%                    | 0%                      | 0%          |
