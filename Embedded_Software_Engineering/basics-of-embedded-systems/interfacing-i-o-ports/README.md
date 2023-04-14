---
description: Working with GPIO pins
---

# Interfacing I/O ports

{% hint style="info" %}
Before reading this, it is very important to have a basic understanding of the C Programming language, and a decent knowledge in bitwise operators.
{% endhint %}

## Overview

Registers are a critical feature of any computer processor and are the secret to doing anything with a microcontroller. Put crudely, you make things happen by writing a value to a register. You find out what’s happening (eg, get input) by reading the values in registers. And a register is essentially just a location within the microcontroller’s address space.

Interfacing I/O ports in an AVR microcontroller involves configuring the microcontroller's pins to act as inputs or outputs, and then reading or writing data to those pins. The ATMEGA128 has a total of 86 I/O pins, which are organized into several different ports (PORTA, PORTB, PORTC, PORTD, PORTE, PORTF, and PORTG).

Each port on the AVR has three associated registers: DDR, PIN, and PORT.&#x20;

The DDRx register stands for (**Data Direction Register**), which is used to set the direction of the data flow for each pin in the port. Each bit in the DDR register corresponds to one pin in the port. When a bit in the DDR register is set to 1, it configures the corresponding pin as an output pin. When a bit in the DDR register is set to 0, it configures the corresponding pin as an input pin.

The (**Port Output Register**) PORTx, is used to control the output value of each pin in the port. Each bit in the PORT register corresponds to one pin in the port. When a bit in the PORT register is set to 1, it sets the corresponding output pin to a logic high level. When a bit in the PORT register is set to 0, it sets the corresponding output pin to a logic low level.

The (**Port Input Register**) PINx, is used for reading the input value of each pin.\

### Controlling Data Direction

We usually think in binary when we work with registers, because each bit within the byte located at address DDRx represents a separate pin. To set a pin as input you write 0 to the relevant bit. To set it as output you write a 1. Here are a few examples:

```clike
// Setting the direction of all pins of port C as input
DDRC = 0b00000000;

// Set pin (2) only as output of port B:
DDRB = 0b00000100;
```

That’s fairly clear, but it has a downside. At the same time as setting pin 2 as an output it also sets all the other pins as inputs – which may not be the effect you’re after! Generally, it’s good practice to focus purely on the pin in question and not risk side effects.

As a good practice, we usually write code that highlights only the pin in question, so we use such syntax:

```c
DDRB |= (1 << PB2)
```

Let's decompose this expression:

**OR `DDRB |= val`**

In this code, we're ORing the register itself with another \`val\`, so it is exactly equivalent to this:  `DDRB = DDRB | val` to achieve our purpose and set pin 2 as output in particular and leave the rest of the pins the same without making any changes to them, we do so: `DDRB = DDRB | 0b00000100` So basically we are just leaving all pins on their original state and only updating the pin 2 of port B as output.

**Bit shifting `(1 << PB2)`**

Bit shifting here plays a major role in improving code readability and achieving our purpose, `PB2` is just a macro that have the value 2, Yes, that's basically what it is, just a macro for number 2! So, basically we move the bit 1 3 steps to the left (at index 2), so that `(1 << PB2)` is equivalent to `0b00000100`&#x20;

In case if you're wondering, where all these things come from `DDRB`, `PB2`, these are all macros defined within the AVR library that you should include at the beginning of your code

```c
#include <avr/io.h>
```

**What about going the otherway? Setting the bit 2 of port B to be an input pin (clearing the bit)?**

Again, we will make use of the logical operators to achieve this purpose, this time we are going to use the AND operator:

```c
DDRB &= ~(1 << PB2)
```

Let's dissect this expression:

* `(1 << PB2)` as we mentioned before is equivalent to `0b00000100`
* `~(1 << PB2)` In this expression, we are just complementing the binary number, so the end result should be `0b11111011`
* `DDRB &= ~(1 << PB2)` Eventually we AND the register with the resulting binary number, keep in mind, when we AND any bit with value (1) we get the same exact value of this bit without any changes, otherwise, if we AND'd any bit x with 0, we clear the bit x (setting its value to zero) whatever that bit value is.
