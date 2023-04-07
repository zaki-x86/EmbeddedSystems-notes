---
description: This project is the hello world for embedded systems
---

# Embedded Systems 101: Blinking a LED

Since we know understand how to program the AVR pins, we can now blink a LED. This project is the hello world for embedded systems.

## Components

- [ATMEGA328P](https://www.sparkfun.com/products/11021)
- [LED](https://www.sparkfun.com/products/106)
- [Resistor](https://www.sparkfun.com/products/12006)
- [Breadboard](https://www.sparkfun.com/products/12002)
- [Breadboard Jumper Wires](https://www.sparkfun.com/products/12001)

## Circuit

![LED connected to AVR circuit diagram]()

## Code

```c
#include <avr/io.h>
#include <util/delay.h>

int main(void) {
    DDRB |= (1 << DDB5); // Set PB5 as output

    while (1) {
        PORTB |= (1 << PB5); // Set PB5 high
        _delay_ms(1000); // Wait 1000ms

        PORTB &= ~(1 << PB5); // Set PB5 low
        _delay_ms(1000); // Wait 1000ms
    }
}
```
