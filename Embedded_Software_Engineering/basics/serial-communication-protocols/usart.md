---
description: Understanding how to use the USART
---

# USART / UART

Universal Synchronous/Asynchronous Receiver/Transmitter or UART for short represents the hardware circuitry (module) being used for serial communication. UART is sold/shipped as a standalone integrated circuit (IC) or as an internal module within microcontrollers.

There are two forms of UART hardware:

- UART – Universal Asynchronous Receiver/Transmitter
- USART – Universal Synchronous/Asynchronous Receiver/Transmitter

The Synchronous type of transmitters generates the data clock and sends it to the receiver which works accordingly in a synchronized manner. On the other hand, the Asynchronous type of transmitter generates the data clock internally. There is no incoming serial clock signal, so in order to achieve proper communication between the two ends, both of them must be using the same **baud rate**.

Like many microcontrollers AVR has a dedicated hardware for USART.

This special hardware make your life as programmer easier. You just have to supply the data you need to transmit and it will do the rest.

## USART Pinout

The following table shows the pinout of the USART.

| Pin | Description |
| --- | ----------- |
| TX | Transmit |
| RX | Receive |
| GND | Ground |

## USART Data Packet

The data frame is the data that is being transmitted or received. The data frame consists of the following:

- Start bit
- Data bits
- Parity bit
- Stop bit

### Start Bit

The start bit is a single bit that is always `0`. It is used to indicate the start of the data frame.

The UART data transmission line (TX) is normally held High (1) logic-level when there is no data transmission on the line. To start data transfer, the transmitting UART pulls-down the transmission line from high to low for one clock cycle. When the receiving UART module detects the high to low voltage transition, it begins reading the incoming bits of the entire data frame at the same frequency of the specified baud rate.

### Data Bits

The data bits are the bits that carry the actual data. The number of data bits can be 5, 6, 7, or 8 bits.

### Parity Bit

The parity bit is used to check for errors in the data frame. The parity bit can be either even or odd. If the parity bit is even, then the number of `1` bits in the data frame must be even. If the parity bit is odd, then the number of `1` bits in the data frame must be odd.

### Stop Bit

The stop bit is a single bit that is always `1`. It is used to indicate the end of the data frame.

## USART Data Transfer Rate

### Baud Rate

The Baud Rate specifies how fast the data is sent over the bus and it is specified in bits-per-second or bps. You can actually choose any speed for the baud rate. However, there are some specific values that are known to be the industry standards. The most common and widely-used standardized value is 9600. Other standard baud rates include: 1200, 2400, 4800, 19200, 38400, 57600 and 115200. Obviously, baud rates are always multiples of 300. Baud rates higher than 115200(bps) can be used with an additional probability of having, at best, missing data packets. The rule of thumb in UART communication is, both the transmitter and the Receiver UART must agree on the exact same Baud Rate for a successful data transmission.

### USART Registers

As a software engineer you don't have to be concerned with the intricate details of the hardware. You just have to know how to use it. The following table shows the registers used for USART.

| Register | Description |
| -------- | ----------- |
| UDR | USART I/O Data Register |
| UCSRA | USART Control and Status Register A |
| UCSRB | USART Control and Status Register B |
| UCSRC | USART Control and Status Register C |

Checkout the datasheet for more details on the registers: [USART Register Description | Microchip](https://onlinedocs.microchip.com/pr/GUID-80B1922D-872B-40C8-A8A5-0CBE009FD908-en-US-3/index.html?GUID-F721DB7D-EB3A-490F-A762-AA8C7CC06CD5)

#### UDR – USART I/O Data Register

The UDR register is used to read and write data to the USART.

The USART Transmit Data Buffer Register and USART Receive Data Buffer Registers share the same I/O address referred to as USART Data Register or `UDR`.

#### USART Control and Status Register A (UCSRA)

The UCSRA register is used to control the USART and provide status flags. The following table shows the bits in the register.

| Bit | Description |
| --- | ----------- |
| MPCM | Multi-processor Communication Mode |
| U2X | Double the USART Transmission Speed |
| UPE | Parity Error |
| DOR | Data overRun |
| FE | Framing Error |
| UDRE | USART Data Register Empty |
| TXC | USART Transmitt Complete |
| RXC | USART Receive Complete |

#### USART Control and Status Register B (UCSRB)

The UCSRB register is used to control the USART. The following table shows the bits in the register.

| Bit | Description |
| --- | ----------- |
|RXCIE | RX Complete Interrupt Enable |
| TXCIE | TX Complete Interrupt Enable |
| UDRIE | USART Data Register Empty Interrupt Enable |
| RXEN | Receiver Enable |
| TXEN | Transmitter Enable |
| UCSZ2 | Character Size |
| TXB8 | Transmit Data Bit 8 |
| RXB8 | Receive Data Bit 8 |

#### USART Control and Status Register C (UCSRC)

The UCSRC register is used to control the USART. The following table shows the bits in the register.

| Bit | Description |
| --- | ----------- |
| UMSEL | USART Mode Select |
| UPM0 | Parity Mode |
| UPM1 | Parity Mode |
| USBS | Stop Bit Select |
| UCSZ0 | Character Size |
| UCSZ1 | Character Size |
| UCPOL | Clock Polarity |

#### USART Baud Rate Register (UBRR)

The UBRR register is used to set the baud rate of the USART. The following table shows the bits in the register.

| Bit | Description |
| --- | ----------- |
| UBRRH | USART Baud Rate Register High |
| UBRRL | USART Baud Rate Register Low |

## The Data Transmission Process

### Initialization

The first step is to initialize the USART. The following code shows how to initialize the USART.

```c
#include <avr/io.h>
#include <util/delay.h>

void USART_Init(unsigned int ubrr)
{
    /* Set baud rate */
    UBRRH = (unsigned char)(ubrr>>8);
    UBRRL = (unsigned char)ubrr;
    /* Enable receiver and transmitter */
    UCSRB = (1<<RXEN)|(1<<TXEN);
    /* Set frame format: 8data, 2stop bit */
    UCSRC = (1<<URSEL)|(1<<USBS)|(3<<UCSZ0);
}

int main(void)
{
    USART_Init(51);
    while(1)
    {
        // application logic goes here
    }
    return 0;
}
```

### Transmitting Data

#### Sending frames with 5 to 8 data bits

The following code shows how to transmit data.

```c
void USART_Transmit(unsigned char data)
{
    /* Wait for empty transmit buffer */
    while ( !( UCSRA & (1<<UDRE)) );
    /* Put data into buffer, sends the data */
    UDR = data;
}
```

#### Sending frames with 9 data bits

```c
void USART_Transmit( unsigned int data )
{
    /* Wait for empty transmit buffer */
    while ( !( UCSRnA & (1<<UDRE))) );
    
    /* Copy 9th bit to TXB8 */
    UCSRB &= ~(1<<TXB8);
    if ( data & 0x0100 )
        UCSRnB |= (1<<TXB8);
    /* Put data into buffer, sends the data */
    UDR = data;
}
```

### Receive Data

#### Receiving frames with 5 to 8 data bits

The following code shows how to receive data.

```c
unsigned char USART_Receive(void)
{
    /* Wait for data to be received */
    while ( !(UCSRA & (1<<RXC)) );
    /* Get and return received data from buffer */
    return UDR;
}
```

#### Receiving frames with 9 data bits

```c
unsigned int USART_Receive( void )
{
    unsigned char status, resh, resl;
    /* Wait for data to be received */
    while ( !(UCSRnA & (1<<RXC)) );
    /* Get status and 9th bit, then data */
    /* from buffer */
    status = UCSRnA;
    resh = UCSRnB;
    resl = UDR;
    /* If error, return -1 */
    if ( status & ((1<<FE)|(1<<DOR)|(1<<PE)) )
        return -1;
    /* Filter the 9th bit, then return */
    resh = (resh >> 1) & 0x01;
    return ((resh << 8) | resl);
}
```

## Example: Serial Monitor

## References

- [Interrupt-driven UART Library for 8-bit AVR](https://onlinedocs.microchip.com/pr/GUID-80B1922D-872B-40C8-A8A5-0CBE009FD908-en-US-3/index.html?GUID-F721DB7D-EB3A-490F-A762-AA8C7CC06CD5)