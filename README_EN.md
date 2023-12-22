This is an automatic translation, may be incorrect in some places. See sources and examples!

# Timerandom
Library for generating a set of random numbers with a binding to the time
- allows you to generate the same random numbers on different devices synchronized in time

## compatibility
Compatible with all arduino platforms (used arduino functions)

## Content
- [installation] (# Install)
- [initialization] (#init)
- [use] (#usage)
- [Example] (# Example)
- [versions] (#varsions)
- [bugs and feedback] (#fedback)

<a id="install"> </a>
## Installation
- The library can be found by the name ** Timerandom ** and installed through the library manager in:
    - Arduino ide
    - Arduino ide v2
    - Platformio
- [download the library] (https://github.com/gyverlibs/timorandom/archive/refs/heads/main.zip) .Zip archive for manual installation:
    - unpack and put in * C: \ Program Files (X86) \ Arduino \ Libraries * (Windows X64)
    - unpack and put in * C: \ Program Files \ Arduino \ Libraries * (Windows X32)
    - unpack and put in *documents/arduino/libraries/ *
    - (Arduino id) Automatic installation from. Zip: * sketch/connect the library/add .Zip library ... * and specify downloaded archive
- Read more detailed instructions for installing libraries [here] (https://alexgyver.ru/arduino-first/#%D0%A3%D1%81%D1%82%D0%B0%BD%D0%BE%BE%BE%BED0%B2%D0%BA%D0%B0_%D0%B1%D0%B8%D0%B1%D0%BB%D0%B8%D0%BE%D1%82%D0%B5%D0%BA)
### Update
- I recommend always updating the library: errors and bugs are corrected in the new versions, as well as optimization and new features are added
- through the IDE library manager: find the library how to install and click "update"
- Manually: ** remove the folder with the old version **, and then put a new one in its place.“Replacement” cannot be done: sometimes in new versions, files that remain when replacing are deleted and can lead to errors!


<a id="init"> </a>
## initialization
`` `CPP
Timerandom rnd;
`` `

<a id="usage"> </a>
## Usage
`` `CPP
VOID setchannel (Uint8_t Channel);// Install the channel (by silence 0)
VOID update (uint8_t h, uint8_t m, uint8_t s);// Update the CMS
uint32_t getsec ();// The number of seconds from the beginning of the day
uint32_t getmin ();// The number of minutes from the beginning of the day
Uint16_T FromSec (Int EVERY);// random number, is updated every EVEY seconds
uint16_t fromSec (Uint8_t EVERY, UINT16_T MAX);// random number from 0 to max, is updated every EVERY of seconds
uint16_t fromSec (Uint8_t EVERY, UINT16_T MIN, UINT16_T MAX);// random number from Min to Max, is updated every EVEY of seconds
Uint16_T Frommin (Ints);// random number, is updated every EVERY minutes
Uint16_T Frommin (Uint8_t EVERY, UINT16_T MAX);// random number from 0 to max, is updated every EVERY minutes
Uint16_t Frommin (Uint8_t EVERY, UINT16_T MIN, UINT16_T MAX);// random number from min to max, is updated every EVERY minutes
`` `

<a id="EXAMPLE"> </a>
## Example
`` `CPP
#include <timorandom.h>

Timerandom rnd;

VOID setup () {
  Serial.Begin (9600);
}

byte hor = 0;
byte minute = 0;
Byte second = 0;

VOID loop () {
  if (++ second> = 60) {
    second = 0;if (++ minute> = 60) {
      minute = 0;
      if (++ hour> = 24) {
        Hour = 0;
      }
    }
  }
  rnd.update (hor, minute, second);
  Serial.println (rnd.fromsec (2, 0, 10));
  Delay (10);
}
`` `

<a id="versions"> </a>
## versions
- V1.0

<a id="feedback"> </a>
## bugs and feedback
Create ** Issue ** when you find the bugs, and better immediately write to the mail [alex@alexgyver.ru] (mailto: alex@alexgyver.ru)
The library is open for refinement and your ** pull Request ** 'ow!


When reporting about bugs or incorrect work of the library, it is necessary to indicate:
- The version of the library
- What is MK used
- SDK version (for ESP)
- version of Arduino ide
- whether the built -in examples work correctly, in which the functions and designs are used, leading to a bug in your code
- what code has been loaded, what work was expected from it and how it works in reality
- Ideally, attach the minimum code in which the bug is observed.Not a canvas of a thousand lines, but a minimum code