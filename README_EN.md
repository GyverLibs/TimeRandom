This is an automatic translation, may be incorrect in some places. See sources and examples!

# TimeRandom
Library for generating a set of random numbers with reference to time
- Allows you to generate the same random numbers on different devices synchronized in time

### Compatibility
Compatible with all Arduino platforms (using Arduino functions)

## Content
- [Install](#install)
- [Initialization](#init)
- [Usage](#usage)
- [Example](#example)
- [Versions](#versions)
- [Bugs and feedback](#feedback)

<a id="install"></a>
## Installation
- The library can be found by the name **TimeRandom** and installed through the library manager in:
    - Arduino IDE
    - Arduino IDE v2
    - PlatformIO
- [Download library](https://github.com/GyverLibs/TimeRandom/archive/refs/heads/main.zip) .zip archive for manual installation:
    - Unzip and put in *C:\Program Files (x86)\Arduino\libraries* (Windows x64)
    - Unzip and put in *C:\Program Files\Arduino\libraries* (Windows x32)
    - Unpack and put in *Documents/Arduino/libraries/*
    - (Arduino IDE) automatic installation from .zip: *Sketch/Include library/Add .ZIP library…* and specify the downloaded archive
- Read more detailed instructions for installing libraries [here] (https://alexgyver.ru/arduino-first/#%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE% D0%B2%D0%BA%D0%B0_%D0%B1%D0%B8%D0%B1%D0%BB%D0%B8%D0%BE%D1%82%D0%B5%D0%BA)

<a id="init"></a>
## Initialization
```cpp
TimeRandom rnd;
```

<a id="usage"></a>
## Usage
```cpp
void setChannel(uint8_t channel); // set channel (default 0)
void update(uint8_t h, uint8_t m, uint8_t s); // update hms
uint32_t getSec(); // number of seconds since the beginning of the day
uint32_t getMin(); // number of minutes since the beginning of the day
uint16_t fromSec(int every); // random number, updated every second
uint16_t fromSec(uint8_t every, uint16_t max); // random number from 0 to max, updated every second
uint16_t fromSec(uint8_t every, uint16_t min, uint16_t max); // random number from min to max, updated every second
uint16_t fromMin(int every); // random number, updated every every minutes
uint16_t fromMin(uint8_t every, uint16_t max); // random number from 0 to max, updated every every minutes
uint16_t fromMin(uint8_t every, uint16_t min, uint16_t max); // random number from min to max, updated every minute
```

<a id="example"></a>
## Example
```cpp
#include <TimeRandom.h>

TimeRandom rnd;

void setup() {
  Serial.begin(9600);
}

byte hour = 0;
byte minute = 0;
byte second = 0;

void loop() {
  if (++second >= 60) {
    second = 0;
    if (++minute >= 60) {
      minutes = 0;
      if (++hour >= 24) {
        hours = 0;
      }
    }
  }
  rnd.update(hour, minute, second);
  Serial.println(rnd.fromSec(2, 0, 10));
  delay(10);
}
```

<a id="versions"></a>
## Versions
- v1.0

<a id="feedback"></a>
## Bugs and feedback
When you find bugs, create an **Issue**, or better, immediately write to the mail [alex@alexgyver.ru](mailto:alex@alexgyver.ru)
The library is open for revision and your **Pull Request**'s!