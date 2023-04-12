---
title: "LCD Interfacing with AVR"
date: 2023-03-25
author: ["M Zaki"]
categories: ["AVR"]
keywords: ["AVR", "LCD", "Embedded Systems"]
---

# LCD Interfacing with ATMEGA32

## What IS LCD?

LCD stands for Liquid Crystal Display, is an electronic device which is used for data display. LCDs are preferable over seven segments and LEDs as they can easily represent data in form of alphabets, characters, numbers or animations. LCDs are very easy to program and make your work quite attractive and simple. Numerous types of LCDs are available in market such as 16X2, 16X4, 20X2, 20X4, graphical LCDs (128X64) etc. The LCD which we are using is 16X2 alphanumeric LCD, it display 32 characters in two rows means in one row we have 16 characters.

## Pin Configuration of LCD

LCD has 16 pins, 14 pins are used for data transfer and 2 pins are used for power supply. The pin configuration of LCD is shown in the table below.

| Pin No. | Pin Name | Description |
| --- | --- | --- |
| 1 | VSS | Ground |
| 2 | VDD | Power Supply |
| 3 | V0 | Contrast Adjustment |
| 4 | RS | Register Select: 0 -> instruction, 1 -> data |
| 5 | RW | Read/Write: 0 -> write, 1 -> read |
| 6 | E | Enable |
| 7 | DB0 : DB7 | Data Bus |
| 8 | A | Anode |
| 9 | K | Cathode |

LCD accepts two types of signals, one is instruction and other is data. The instruction is used to control the LCD and data is used to display the data on LCD. The `RS` pin is used to select the type of signal, if `RS` is low then the signal is instruction and if `RS` is high then the signal is data. The `RW` pin is used to select the direction of data transfer, if `RW` is low then the data is transferred from microcontroller to LCD and if `RW` is high then the data is transferred from LCD to microcontroller. The `E` pin is used to enable the LCD. As soon as the E pin is pulsed, LCD display reads data at the falling edge of the pulse and executes it, same for the case of transmission. The DB0 : DB7 pins are used to transfer data from microcontroller to LCD. The A pin is used to supply power to LCD and K pin is used to ground the LCD.

LCD display takes a time of $39-43µS$ to place a character or execute a command. Except for clearing display and to seek cursor to home position it takes 1.53ms to 1.64ms. Any attempt to send any data before this interval may lead to failure to read data or execution of the current data in some devices. Some devices compensate the speed by storing the incoming data to some temporary registers.

LCD displays have two RAMs, naming **DDRAM** and **CGRAM**.

### 1. DDRAM

In the 16x2 LCD, the DDRAM consists of 80 bytes of memory, and each byte can be used to store a single character. This means that you can store up to 80 characters in the DDRAM. The DDRAM is used to store the characters that are to be displayed on the LCD. The DDRAM is accessed by sending the command `0x80` to the LCD. The DDRAM address is automatically incremented after each byte is written. The DDRAM address is automatically reset to `0x00` after the last byte of the DDRAM is written.

### 2. CGRAM

In the 16x2 LCD, the CGRAM consists of 64 bytes of memory, and each byte can be used to define a single 5x8 dot custom character. This means that you can define up to 8 custom characters in the CGRAM, since each custom character takes up 8 bytes (i.e., 8 consecutive addresses) of the CGRAM. The CGRAM is used to store the custom characters. The CGRAM is accessed by sending the command `0x40` to the LCD. The CGRAM address is automatically incremented after each byte is written. The CGRAM address is automatically reset to `0x00` after the last byte of the CGRAM is written.


## LCD Instruction Set

Each instruction consists of 3 control bits and 8 data bits. The control bits are `RS`, `RW` and `E`. The data bits are `DB0 : DB7`. The instruction set of LCD is shown below.

In order to send instructions to the LCD, both `RS` and `RW` pins must be low. The `E` pin is used to enable the LCD before sending the instruction. After sending the instruction, `E` pin must be pulsed again to disable the LCD. The instruction set is shown in the table below.

The LCD instruct consists of 2 parts; the first 4-bits represents the specific command that needs to be executed and the second 4-bits represents command parameters that provide additional information to the command. The command parameters are optional and are not always required.

### 1. Clear Display

This instruction clears the entire display and sets the DDRAM address 0 in address counter. The DDRAM contents remain unchanged. The address counter is set to address 0.

| Instruction | Binary | Hex |
| --- | --- | --- |
| Clear Display | **0b**0000 0001 | **0x**01 |

### 2. Return Home

This instruction sets the DDRAM address 0 in address counter. Also returns display from being shifted to original position. DDRAM contents remain unchanged.

| Instruction | Binary | Hex |
| --- | --- | --- |
| Return Home | **0b**0000 0010 | **0x**02 |

### 3. Entry Mode Set

This instruction sets the cursor move direction and specifies display shift. These operations are performed during data write and read.

| Instruction | Binary | Hex |
| --- | --- | --- |
| Entry Mode Set | **0b**0000 01(I/D)S | depending on I/D and S |

| Bit | Description |
| --- | --- |
| I/D | 1 -> Increment, 0 -> Decrement |
| S | 1 -> Display shift on, 0 -> Display shift off |

### 4. Display On/Off Control

This instruction sets the entire display on/off, cursor on/off, and blinking of cursor position character.

| Instruction | Binary | Hex |
| --- | --- | --- |
| Display On/Off Control | **0b**00001DCB | depending on D, C and B |

| Bit | Description |
| --- | --- |
| D | 1 -> Display on, 0 -> Display off |
| C | 1 -> Cursor on, 0 -> Cursor off |
| B | 1 -> Blinking on, 0 -> Blinking off |

### 5. Cursor or Display Shift

This instruction shifts the cursor and shifts the display without changing the DDRAM contents.

| Instruction | Binary | Hex |
| --- | --- | --- |
| Cursor or Display Shift | **0b**0001SCRL | depending on S/C and R/L |

| Bit | Description |
| --- | --- |
| S/C | 1 -> Display shift, 0 -> Cursor move |
| R/L | 1 -> Shift to right, 0 -> Shift to left |

### 6. Function Set

This instruction sets the interface data length, number of display lines, and character font.

| Instruction | Binary | Hex |
| --- | --- | --- |
| Function Set | **0b**001(DL)NF | depending on DL, N and F |

| Bit | Description |
| --- | --- |
| DL | 1 -> 8-bit interface data, 0 -> 4-bit interface data |
| N | 1 -> 2-line display, 0 -> 1-line display |
| F | 1 -> 5x10 dots character font, 0 -> 5x8 dots character font |

### 7. Set CGRAM Address

This instruction sets the CGRAM address. CGRAM data is sent and received after this setting.

| Instruction | Binary | Hex |
| --- | --- | --- |
| Set CGRAM Address | 01(AC AC AC AC AC AC) | starts from 0x40 |

The set CGRAM instruction can be thought of as (0b0100 0000 + 6-bit-address). The address is 6 bits long, so the maximum address is 0b111111. The CGRAM address is 0x40 to 0x7F.

### 8. Set DDRAM Address

This instruction sets the DDRAM address. DDRAM data is sent and received after this setting.

| Instruction | Binary | Hex |
| --- | --- | --- |
| Set DDRAM Address | 1(AC AC AC AC AC AC) | starts from 0x00 |

The set DDRAM instruction can be thought of as (0b1000 0000 + 7-bit-address). The address is 7 bits long, so the maximum address is 0b1111111. The DDRAM address is 0x00 to 0x7F.

## LCD Interfacing

![LCD interfacing 4-bit mode](https://www.circuitstoday.com/wp-content/uploads/2012/02/LCD-Display-Interfacing-Flowchart.png)

**Source**: [Circuitstoday](http://www.circuitstoday.com/a-note-on-character-lcd-displays)

It's always good practice to setup macros for the LCD instructions:

```c
// LCD Control Pins
// These are the pins that are connected to the LCD
// Users of the library manually define these pins
#define LCD_RS 
#define LCD_RW 
#define LCD_E 

// LCD Instructions
#define LCD_CLEAR_DISPLAY 0x01
#define LCD_RETURN_HOME 0x02
#define LCD_ENTRY_MODE_SET 0x04
#define LCD_DISPLAY_CONTROL 0x08
#define LCD_CURSOR_SHIFT 0x10
#define LCD_FUNCTION_SET 0x20
#define LCD_SET_CGRAM_ADDR 0x40
#define LCD_SET_DDRAM_ADDR 0x80

// LCD Entry Mode Set
#define LCD_ENTRY_MODE_INCREMENT 0x02
#define LCD_ENTRY_MODE_DECREMENT 0x00
#define LCD_ENTRY_MODE_DISPLAY_SHIFT_ON 0x01
#define LCD_ENTRY_MODE_DISPLAY_SHIFT_OFF 0x00

// LCD Display On/Off Control
#define LCD_DISPLAY_ON 0x04
#define LCD_DISPLAY_OFF 0x00
#define LCD_CURSOR_ON 0x02
#define LCD_CURSOR_OFF 0x00
#define LCD_BLINKING_ON 0x01
#define LCD_BLINKING_OFF 0x00

// LCD Cursor or Display Shift
#define LCD_DISPLAY_SHIFT 0x08
#define LCD_CURSOR_MOVE 0x00
#define LCD_SHIFT_TO_RIGHT 0x04
#define LCD_SHIFT_TO_LEFT 0x00

// LCD Function Set
#define LCD_8BIT 0x10
#define LCD_4BIT 0x00
#define LCD_2LINE 0x08
#define LCD_1LINE 0x00
#define LCD_5x10DOTS 0x04
#define LCD_5x8DOTS 0x00

// LCD Data Write
#define LCD_DATA_WRITE 0x80
```

What we have done here is to define the instructions in a way that is easy to understand. These definitions are not concrete, and you can change them to whatever you want. The only thing that matters is that you understand what each instruction does.

### LCD Initialization

![LCD Init](https://www.circuitstoday.com/wp-content/uploads/2012/02/LCD-Intialization-Flow-Chart.png)
**Source**: [Circuitstoday](http://www.circuitstoday.com/a-note-on-character-lcd-displays)

Before using LCD (or any other component) in your circuit, you must check its datasheet for instructions on how to initialize it. The initialization sequence is different for different LCDs. The initialization sequence for the 16x2 LCD-016N002B-CFH-ET can be found [here](https://www.vishay.com/docs/37484/lcd016n002bcfhet.pdf)

Once you fully understand the initialization sequence, you can implement it in your code.

Here is a sample for the implementation of the initialization sequence:

```c
void lcd_init(void) {
    // Wait for more than 15ms after Vcc rises to 4.5V
    _delay_ms(20);

    // Function Set
    lcd_send_command(LCD_FUNCTION_SET | LCD_8BIT | LCD_2LINE | LCD_5x8DOTS);
    _delay_ms(5);

    // Display On/Off Control
    lcd_send_command(LCD_DISPLAY_CONTROL | LCD_DISPLAY_OFF | LCD_CURSOR_OFF | LCD_BLINKING_OFF);
    _delay_us(100);


    // Entry Mode Set
    lcd_send_command(LCD_ENTRY_MODE_SET | LCD_ENTRY_MODE_INCREMENT | LCD_ENTRY_MODE_DISPLAY_SHIFT_OFF);
    _delay_us(100);

    // Clear Display
    lcd_send_command(LCD_CLEAR_DISPLAY);
    _delay_ms(2);
}
```

### Sending a command to the LCD

The LCD has 3 pins that are used to send commands to it: RS, RW, and E. The RS pin is used to select between sending a command or sending data. The RW pin is used to select between reading or writing. The E pin is used to enable the LCD to read or write the data.

We follow the following steps to send a command to the LCD:

1. Set the RS pin to 0
2. Set the RW pin to 0
3. Set the E pin to 1
4. Write the command to the data pins
5. Set the E pin to 0
6. Wait for more than 37us

Here is a sample for the implementation of sending a command to the LCD:

```c
void lcd_send_command(uint8_t command) {
    // Set RS to 0
    // Set RW to 0
    // Set E to 1
    // Write the command to the data pins
    // Set E to 0
    // Wait for more than 37us
}
```

### LCD Data Write

The LCD data write instruction is used to write data to the DDRAM. The data is written to the address specified by the DDRAM address counter. The DDRAM address counter is incremented automatically after each write operation.

The LCD data write instruction can be thought of as (0b1000 0000 + 8-bit-data). The data is 8 bits long, so the maximum data is 0b11111111. The DDRAM address is 0x00 to 0x27.

Here are the exact steps to implement the LCD data write instruction:

1. Set the RS pin to 1
2. Set the RW pin to 0
3. Set the E pin to 1
4. Write the data to the data pins
5. Set the E pin to 0
6. Wait for more than 37us

Here is a sample for the implementation of the LCD data write instruction:

```c
// Here we assume these macros are defined: LCD_RS, LCD_RW, LCD_E
// We also assume these instruction macros are defined: LCD_DATA_WRITE, LCD_SET_DDRAM_ADDR, LCD_CLEAR_DISPLAY, LCD_RETURN_HOME
// We also assume these functions are defined: lcd_send_command, lcd_send_data
