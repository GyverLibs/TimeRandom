[![Foo](https://img.shields.io/badge/Version-1.0-brightgreen.svg?style=flat-square)](#versions)
[![Foo](https://img.shields.io/badge/Website-AlexGyver.ru-blue.svg?style=flat-square)](https://alexgyver.ru/)
[![Foo](https://img.shields.io/badge/%E2%82%BD$%E2%82%AC%20%D0%9D%D0%B0%20%D0%BF%D0%B8%D0%B2%D0%BE-%D1%81%20%D1%80%D1%8B%D0%B1%D0%BA%D0%BE%D0%B9-orange.svg?style=flat-square)](https://alexgyver.ru/support_alex/)

[![Foo](https://img.shields.io/badge/README-ENGLISH-brightgreen.svg?style=for-the-badge)](https://github-com.translate.goog/GyverLibs/TimeRandom?_x_tr_sl=ru&_x_tr_tl=en)

# TimeRandom
Библиотека для генерации набора случайных чисел с привязкой ко времени
- Позволяет генерировать одинаковые случайные числа на разных устройствах, синхронизированных по времени

### Совместимость
Совместима со всеми Arduino платформами (используются Arduino-функции)

## Содержание
- [Установка](#install)
- [Инициализация](#init)
- [Использование](#usage)
- [Пример](#example)
- [Версии](#versions)
- [Баги и обратная связь](#feedback)

<a id="install"></a>
## Установка
- Библиотеку можно найти по названию **TimeRandom** и установить через менеджер библиотек в:
    - Arduino IDE
    - Arduino IDE v2
    - PlatformIO
- [Скачать библиотеку](https://github.com/GyverLibs/TimeRandom/archive/refs/heads/main.zip) .zip архивом для ручной установки:
    - Распаковать и положить в *C:\Program Files (x86)\Arduino\libraries* (Windows x64)
    - Распаковать и положить в *C:\Program Files\Arduino\libraries* (Windows x32)
    - Распаковать и положить в *Документы/Arduino/libraries/*
    - (Arduino IDE) автоматическая установка из .zip: *Скетч/Подключить библиотеку/Добавить .ZIP библиотеку…* и указать скачанный архив
- Читай более подробную инструкцию по установке библиотек [здесь](https://alexgyver.ru/arduino-first/#%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0_%D0%B1%D0%B8%D0%B1%D0%BB%D0%B8%D0%BE%D1%82%D0%B5%D0%BA)

<a id="init"></a>
## Инициализация
```cpp
TimeRandom rnd;
```

<a id="usage"></a>
## Использование
```cpp
void setChannel(uint8_t channel);               // установить канал (по умолч 0)
void update(uint8_t h, uint8_t m, uint8_t s);   // обновить ЧМС
uint32_t getSec();                              // количество секунд с начала суток
uint32_t getMin();                              // количество минут с начала суток
uint16_t fromSec(int every);                                    // случайное число, обновляется каждые every секунд
uint16_t fromSec(uint8_t every, uint16_t max);                  // случайное число от 0 до max, обновляется каждые every секунд
uint16_t fromSec(uint8_t every, uint16_t min, uint16_t max);    // случайное число от min до max, обновляется каждые every секунд
uint16_t fromMin(int every);                                    // случайное число, обновляется каждые every минут
uint16_t fromMin(uint8_t every, uint16_t max);                  // случайное число от 0 до max, обновляется каждые every минут
uint16_t fromMin(uint8_t every, uint16_t min, uint16_t max);    // случайное число от min до max, обновляется каждые every минут
```

<a id="example"></a>
## Пример
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
## Версии
- v1.0

<a id="feedback"></a>
## Баги и обратная связь
При нахождении багов создавайте **Issue**, а лучше сразу пишите на почту [alex@alexgyver.ru](mailto:alex@alexgyver.ru)  
Библиотека открыта для доработки и ваших **Pull Request**'ов!