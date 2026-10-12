---
sort: 8
---

# PS1 Controller

Latency of an input from a PS1 Controller.

Measured by connecting it to the microcontroller in question, and then sending a signal to toggle the right trigger input, and timing how long it takes that signal to reach a target device over USB.

| microcontroller | Sparkfun Pro Micro 5V | Sparkfun Pro Micro 3.3V | Arduino Uno |
| :-------------- | :-------------------- | :---------------------- | :---------- |
| poll rate       | 1 ms                  | 1 ms                    | 1 ms        |
| min             | 0.48 ms               | 0.66 ms                 | 1.93 ms     |
| max             | 2.13 ms               | 2.62 ms                 | 3.07 ms     |
| avg             | 1.14 ms               | 1.46 ms                 | 2.43 ms     |
| stddev          | 0.35 ms               | 0.39 ms                 | 0.34 ms     |
| %on time        | 94%                   | 92%                     | 86%         |
| %1f skip        | 6%                    | 8%                      | 14%         |
| %2f skip        | 0%                    | 0%                      | 0%          |
| %3f skip        | 0%                    | 0%                      | 0%          |
