---
sort: 1
---

# Direct
Latency of directly hooking an input to a digital pin on a microcontroller

Measured by toggling a pin on the microcontroller in question, and then timing how long it takes for that signal to reach a target over USB.

| Microcontroller | Sparkfun Pro Micro 5V | Sparkfun Pro Micro 3.3V | Arduino Uno |
| :-------------- | --------------------- | ----------------------- | ----------- |
| Usb Poll Rate   | 1 ms                  | 1 ms                    | 1 ms        |
| Minimum         | 0.53 ms               | 0.53 ms                 | 0.48 ms     |
| Maximum         | 1.34 ms               | 1.35 ms                 | 1.3 ms      |
| Average         | 0.84 ms               | 0.84 ms                 | 0.8 ms      |
| Std dev         | 0.24 ms               | 0.24 ms                 | 0.25 ms     |
| %on time        | 96%                   | 96%                     | 96%         |
| %1f skip        | 4%                    | 4%                      | 4%          |
| %2f skip        | 0%                    | 0%                      | 0%          |
| %3f skip        | 0%                    | 0%                      | 0%          |
