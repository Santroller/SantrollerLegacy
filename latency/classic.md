---
sort: 4
---

# Wii Classic Controller

Latency of an input from a Wii Classic Controller

Measured by connecting it to the microcontroller in question, and then sending a signal to toggle the "A" button, and timing how long it takes that signal to reach a target device over USB.

| microcontroller | Sparkfun Pro Micro 5V | Sparkfun Pro Micro 3.3V | Arduino Uno | raphnet wusbmote |
| :-------------- | :-------------------- | :---------------------- | :---------- | :--------------- |
| poll rate       | 1 ms                  | 1 ms                    | 1 ms        | 1 ms             |
| min             | 0.53 ms               | 0.62 ms                 | 1.26 ms     | 0.51 ms          |
| max             | 2.94 ms               | 3.7 ms                  | 2.58 ms     | 2.47 ms          |
| avg             | 1.5 ms                | 1.89 ms                 | 1.81 ms     | 1.46 ms          |
| stddev          | 0.5 ms                | 0.61 ms                 | 0.27 ms     | 0.44 ms          |
| %on time        | 92%                   | 89%                     | 90%         | 92%              |
| %1f skip        | 8%                    | 11%                     | 10%         | 8%               |
| %2f skip        | 0%                    | 0%                      | 0%          | 0%               |
| %3f skip        | 0%                    | 0%                      | 0%          | 0%               |
