<<<<<<< HEAD
---
title: "Microcontrollers: The Big Picture"
date: 2023-3-23
author: ["M Zaki"]
keywords: ["Introduction to Microcontrollers", "Embedded Systems"]
---

# Microcontrollers: The Big Picture

- [Microcontrollers: The Big Picture](#microcontrollers-the-big-picture)
  - [A Computer on a Chip](#a-computer-on-a-chip)
  - [Overview of the Microcontroller Hardware](#overview-of-the-microcontroller-hardware)
  - [Overview of the core of an AVR microcontroller](#overview-of-the-core-of-an-avr-microcontroller)
    - [CPU](#cpu)
    - [Memory](#memory)
    - [Clocks](#clocks)
    - [Inputs and Outputs](#inputs-and-outputs)
  - [Overview of the peripherals of an AVR microcontroller](#overview-of-the-peripherals-of-an-avr-microcontroller)
    - [Timers](#timers)
    - [Serial Communication](#serial-communication)
    - [Analog-to-Digital Converter](#analog-to-digital-converter)
    - [Interrupts](#interrupts)
    - [Watchdog Timer](#watchdog-timer)


This is a high-level overview of the microcontroller ecosystem. It is intended to explain the different parts of the ecosystem and how they fit together. It is not intended to be a comprehensive guide to the ecosystem.

## A Computer on a Chip

A microcontroller is a computer on a chip. It is a complete computer, with a CPU, memory, and peripherals, all on a single chip. It is a complete computer because it has all the parts of a computer, but it is a microcontroller because it is designed to be used in a specific way, for a specific purpose, unlike computers which are "general purpose".

Microcontrollers are tiny in size and low in power consumption. They are designed to be used in embedded systems, where they are not the main focus of the system. They are used in a wide variety of applications, from toys to industrial control systems.

Microcontrollers have a very limited memory space, for instance, the flash program memory space in kilobytes in the chip’s name. Yeah, you read that right: we’re talking about 1 KB to 32 KB of room for your code. Because of this limited program memory space, the scope of your program running on a single chip is necessarily smaller than, for example, that Java enterprise banking system you work on in your day job.

Microcontrollers have limited RAM as well, typically 1 KB to 8 KB. This is enough to store a few variables, but not much more. If you need to store more data, you can use the flash memory as a data store, but this is much slower than RAM.

The CPU core clocks of an AVR micoprocessor run from 1 MHz to 20 MHz. This is much slower than the CPU cores in your desktop computer, which run at 2 GHz to 4 GHz. This means that your program will run much slower than your desktop program, but it also means that your program will use much less power.

The raw processing speed of a microcontroller doesn’t hold a candle to a modern PC CPU, but you will be surprised at how much you can do with a few million operations per second.

The AVR which we will be using in this tutorial have 8-bit CPUs with 32 general purpose registers. This means that the CPU can perform 8-bit operations on 8-bit values. It can also perform 16-bit operations on 16-bit values.

Some of the facilities on your PC are not available on a microcontroller. For example, you can’t use a microcontroller to browse the web, or play games, or run a word processor. You can’t even use a microcontroller to run a command line shell. You can’t even use a microcontroller to run a graphical user interface. You can’t even use a microcontroller to run a text editor. There's no operating system, which means no multitasking, no networking, no file system, no drivers, no nothing. But you can get around these limitations by utilizing hardware interrupts, clocks and timers which we will discuss later.

## Overview of the Microcontroller Hardware

The microcontroller does its magic by reading voltage levels on pins and writing voltage levels to the same pins. Blinking an LED is a simple example of this. The microcontroller reads the voltage level on a pin, and if it is high, it writes a low voltage level to the same pin, and if it is low, it writes a high voltage level to the same pin. This causes the LED to blink.

![CHACHIK](https://2.bp.blogspot.com/-87NJwYnX5bA/U3co8YXcPtI/AAAAAAAAEWw/ppWxW4MycgM/s1600/23.PNG)

**Source**: [CHACHIK: ATmega8 Pins](https://echachik.blogspot.com/2014/09/how-to-work-with-avr-mc-pins-and-their.html)

Each pin on the AVR has a name, and you’ll see later on how you can refer to them all in code. So if I hook an LED up to pin number 14, I can then write a high voltage or low voltage out to that pin by referring to it as PB0.

Internally, and somewhat according to function, the pins are arranged into banks of eight pins (they are not located in consecutive blocks).

## Overview of the core of an AVR microcontroller

### CPU

The CPU is the heart of the microcontroller. It is the part that executes the program. The CPU is a 8-bit RISC CPU. RISC stands for [Reduced Instruction Set Computer](https://en.wikipedia.org/wiki/Reduced_instruction_set_computer). It means that the CPU has a small number of instructions, and each instruction is very simple. This makes the CPU very fast, but it also means that the CPU is not very flexible. It is not very good at doing things that are not in its instruction set.

### Memory

The microcontroller has a small amount of memory. It has a small amount of RAM, and a small amount of flash memory. The RAM is used to store variables and other data that is used by the program. The flash memory is used to store the program itself.

The AVR have 3 memory types:

1. **Flash memory**: This is where the program is stored. It is non-volatile, which means that it retains its contents even when the power is turned off. It is also read-only, which means that the program cannot change the contents of the flash memory. The flash memory is used to store the program itself.

2. **EEPROM**: This is where the program can store data that it wants to keep even when the power is turned off. It is non-volatile, which means that it retains its contents even when the power is turned off. It is also read-write, which means that the program can change the contents of the EEPROM. The EEPROM is used to store data that the program wants to keep even when the power is turned off.

3. **RAM**: This is where the program can store data that it wants to keep only as long as the power is on. It is volatile, which means that it loses its contents when the power is turned off. It is also read-write, which means that the program can change the contents of the SRAM. The SRAM is used to store data that the program wants to keep only as long as the power is on.

### Clocks

The clock provides the microcontroller with a sense of time. It is used to keep track of how long the program has been running, and to keep track of how long it has been since the last time a particular event occurred. It is also used to keep track of how long it has been since the last time a particular event occurred.

### Inputs and Outputs

The microcontroller has a number of pins that can be used to read and write data. These pins are used to read and write data to and from the outside world.

## Overview of the peripherals of an AVR microcontroller

Before we begin, what is a peripheral?  a "peripheral" refers to a dedicated hardware module that performs a specific function in a microcontroller or microprocessor system, we will discuss examples of the most common peripherals in the next section:

### Timers

A timer is a device that counts up or down at a fixed rate. It is used to keep track of how long it has been since the last time a particular event occurred.

### Serial Communication

Serial communication provides means to communicate with other devices. For example, you can use serial communication to talk to an accelerometer strapped to your body, and pass the accelerometer data to your microcontroller while you move to render a 3D model of your body in real time.

The AVR has three serial communication interfaces:

1. **USART**: This is useful for communicating with a computer over a serial cable, radio modems, and GPS units.
2. **SPI**: This is useful for ultra-fast communication over short distances with peripherals such as SD cards, flash memory, ADCs, DACs, and other microcontrollers.
3. **I2C**: This is useful for communicating with peripherals such as accelerometers, gyroscopes, and temperature sensors, allowing you to connect up to 127 devices on a single bus.

### Analog-to-Digital Converter

Consider a microphone that outputs a voltage that varies with the sound pressure. You can use an analog-to-digital converter to convert the voltage into a digital value that can be stored in memory, and that your microntroller can understand and process. You can then use a digital-to-analog converter to convert the digital value back into a voltage that can be used to drive a speaker.

### Interrupts

Interrupts provide half the fun of microcontrollers. They enable your program to respond to events that occur outside of the program. For example, you can use an interrupt to respond to a button press, or to respond to a timer expiring, or to respond to a serial communication event.

**Interrupt service routine** is a function that is called when an interrupt occurs. The interrupt service routine is responsible for handling the interrupt, and then returning control to the program.

### Watchdog Timer

The watchdog timer is a timer that is used to reset the microcontroller if the program gets stuck in an infinite loop. It is also used to reset the microcontroller if the program crashes.

---

In the next tutorial, we will learn how to program the AVR microcontroller.

**Next**: [Programming the AVR](./programming-the-avr.md)
=======
# Table of contents

* [Page 1](README.md)
>>>>>>> 7352ef3153ac72a5f70f063cafb9cf2e80e121eb
