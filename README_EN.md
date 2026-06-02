This is an automatic translation and may be incorrect in some places. See the source README and examples for authoritative information.

[![latest](https://img.shields.io/github/v/release/GyverLibs/TimeRandom.svg?color=brightgreen)](https://github.com/GyverLibs/TimeRandom/releases/latest/download/TimeRandom.zip)
[![PIO](https://badges.registry.platformio.org/packages/gyverlibs/library/TimeRandom.svg)](https://registry.platformio.org/libraries/gyverlibs/TimeRandom)
[![Foo](https://img.shields.io/badge/Website-AlexGyver.ru-blue.svg?style=flat-square)](https://alexgyver.ru/)
[![Foo](https://img.shields.io/badge/%E2%82%BD%24%E2%82%AC%20%D0%9F%D0%BE%D0%B4%D0%B4%D0%B5%D1%80%D0%B6%D0%B0%D1%82%D1%8C-%D0%B0%D0%B2%D1%82%D0%BE%D1%80%D0%B0-orange.svg?style=flat-square)](https://alexgyver.ru/support_alex/)
[![Foo](https://img.shields.io/badge/README-ENGLISH-blueviolet.svg?style=flat-square)](https://github-com.translate.goog/GyverLibs/TimeRandom?_x_tr_sl=ru&_x_tr_tl=en)  

[![Foo](https://img.shields.io/badge/ПОДПИСАТЬСЯ-НА%20ОБНОВЛЕНИЯ-brightgreen.svg?style=social&logo=telegram&color=blue)](https://t.me/GyverLibs)

# TimeRandom
A library for generating a set of random numbers with a time reference
- Allows you to generate the same random numbers on different time-synchronized devices

### Compatibility
Compatible with all Arduino platforms (Arduino features are used)

## Contents
- [Installation](#install)
- [Initialization](#init)
- [Use of use](#usage)
- [Example](#example)
- [Versions](#versions)
- [Bugs and feedback](#feedback)

<a id="install"></a>
## Installation
- The library can be found under the name **TimeRandom** and installed through the library manager in:
    - Arduino IDE
    - Arduino IDE v2
    - PlatformIO
- [Download the library](https://github.com/GyverLibs/TimeRandom/archive/refs/heads/main.zip).zip archive for manual installation:
    - Unpack and put in *C:\Program Files (x86)\Arduino\libraries* (Windows x64)
    - Unpack and put in *C:\Program Files\Arduino\libraries* (Windows x32)
    - Unpack and put in *Documents/Arduino/libraries/ *
    - (Arduino IDE) Automatic installation from .zip: *Sketch/Connect library/Add .ZIP library...* and specify downloaded archive
- Read more detailed instructions for installing libraries[here](https://alexgyver.ru/arduino-first/#%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0_%D0%B1%D0%B8%D0%B1%D0%BB%D0%B8%D0%BE%D1%82%D0%B5%D0%BA)
### Update
- I recommend always updating the library: new versions fix errors and bugs, as well as optimize and add new features.
- Through the library manager IDE: find the library as when installing and click "Update"
- Manually: **Delete the folder with the old version** and then put the new one in its place. “Replacement” can not be done: sometimes new versions delete files that will remain when replaced and can lead to errors!

<a id="init"></a>
## Initialization
```cpp
TimeRandom rnd;
```

<a id="usage"></a>
## Use of use
```cpp
void setChannel(uint8_t channel);               // set the channel (by silent 0)
void update(uint8_t h, uint8_t m, uint8_t s);   // upgrade
uint32_t getSec();                              // seconds from the beginning of the day
uint32_t getMin();                              // daytime
uint16_t fromSec(int every);                                    // random number, updated every second
uint16_t fromSec(uint8_t every, uint16_t max);                  // a random number from 0 to max, updated every second
uint16_t fromSec(uint8_t every, uint16_t min, uint16_t max);    // A random number from min to max is updated every second.
uint16_t fromMin(int every);                                    // random number, updated every minute
uint16_t fromMin(uint8_t every, uint16_t max);                  // random number from 0 to max, updated every minute
uint16_t fromMin(uint8_t every, uint16_t min, uint16_t max);    // A random number from min to max is updated every minute.
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
      minute = 0;
      if (++hour >= 24) {
        hour = 0;
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
If you find bugs, create **Issue**, or better write to the mail immediately.[alex@alexgyver.ru](mailto:alex@alexgyver.ru)  
The library is open for revision and your **Pull Requests*!

When reporting bugs or incorrect work of the library, it is necessary to specify:
- Library version
- What is used by the IC
- SDK version (for ESP)
- Arduino IDE version
- Are embedded examples that use features and designs that cause bugs in your code working correctly?
- What code was downloaded, what work was expected from it and how it works in reality
- Ideally, attach the minimum code in which the bug is observed. Not a canvas of a thousand lines, but a minimum code.
