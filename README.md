# libarduino_uno
Arduino lib for pcDuino 8 UNO. Based on pcDuino c_environment.

## Verified Functions

 - GPIO 0~13 (Linker LED + Linker Base)
 - ADC 0~5   (AD7997 adapter + Linker Potentiometer + Linker Base)
 - I2C       (Linker RTC + wires, and Linker Base doesn't work with it)


## TODOs

 - SPI not tested.
 - PWM not implemented.


## How-to

### Installation

Additional package(s) are needed before using libarduino:
```sh
sudo apt-get install libi2c-dev i2c-tools
```

Clean and Compile:
```sh
make clean
make
```

### Create new test program

Create new .c files in sample folder and modify Makefile to compile it. For example I want to create helloLibArduino.c to control an LED on GPIO1.
```C
#include <core.h>
int led_pin = 1;

void setup()
{
  pinMode(led_pin, OUTPUT);
}

void loop()
{
  digitalWrite(led_pin, HIGH); // Turn the LED on
  delay(1000); // Wait for a second
  digitalWrite(led_pin, LOW); // Turn the LED off
  delay(1000); // Wait for a second
}
```

Add a line after OBJS=... and add the name of your program (without .c).
```sh
OBJS = i2c_rtc_test spi_nfc_test adc_test led_test
OBJS += helloLibArduino
```

Compile and run:
```sh
make
sudo output/helloLibArduino
```
Enjoy it!
