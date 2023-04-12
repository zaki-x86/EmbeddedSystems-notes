# SPI (Serial Peripheral Interface)

Serial Peripheral Interface (SPI) is an interface bus commonly used to send data between microcontrollers and small peripherals such as shift registers, sensors, and SD cards. It is primarly used for short distance communication. It uses separate clock and data lines, along with a select line to choose the device you wish to talk to.

## Main SPI Characteristics

* SPI is a master/slave protocol, where the master device initiates communication and the slave devices respond.
* SPI is a full-duplex protocol, meaning that data can be transmitted in both directions at the same time.
* SPI is a synchronous protocol, meaning that data is transmitted with a fixed timing between the transmitter and receiver.
* SPI is a 3-wire protocol, meaning that it uses 3 lines: clock, data, and select.
* LSB or MSB first is configurable.

There are other options that can be configured, such as the clock polarity and phase, but these are not commonly changed.

## SPI Pinout

The SPI interface uses 4 pins: MOSI, MISO, SCK, and SS.

* **MOSI** (Master Out Slave In): The master device sends data to the slave device on this line.
* **MISO** (Master In Slave Out): The slave device sends data to the master device on this line.
* **SCK** (Serial Clock): The clock line. The master device generates the clock signal on this line.
* **SS** (Slave Select): The select line. The master device pulls this line low to select the slave device.

## SPI Communication

![SPI Communication](./images/spi-communication.png)

We can consider the master device and the slave device as two [shift registers](www.wikipedia.org/wiki/Shift_register), and also consider the entire system as if it consists of 2 shift registers and a master clock.
The SPI Master initiates the communication cycle when pulling low the Slave Select SS pin of the desired Slave. Master and Slave prepare the data to be sent in their respective Shift Registers, and the Master generates the required clock pulses on the SCK line to interchange data. Data is always shifted from Master to Slave on the Master Out – Slave In, MOSI, line, and from Slave to Master on the Master In – Slave Out, MISO, line. After each data packet, the Master will synchronize the Slave by pulling high the Slave Select, SS, line.

When SPI is configured as a Master, the SPI interface has no automatic control of the SS line. This must be handled by user software before communication can start. When this is done, writing a byte to the SPI Data Register starts the SPI clock generator, and the hardware shifts the eight bits into the Slave. After shifting one byte, the SPI clock generator stops, setting the end of Transmission Flag (SPIF). If the SPI interrupt enable bit (SPIE) in the SPCR Register is set, an interrupt is requested. The Master may continue to shift the next byte by writing it into SPDR, or signal the end of packet by pulling high the Slave Select, SS line. The last incoming byte will be kept in the Buffer Register for later use.

When configured as a Slave, the SPI interface will remain sleeping with MISO tri-stated as long as the SS pin is driven high. In this state, software may update the contents of the SPI Data Register, SPDR, but the data will not be shifted out by incoming clock pulses on the SCK pin until the SS pin is driven low. As one byte has been completely shifted, the end of Transmission Flag, SPIF is set. If the SPI Interrupt Enable bit, SPIE, in the SPCR Register is set, an interrupt is requested. The Slave may continue to place new data to be sent into SPDR before reading the incoming data. The last incoming byte will be kept in the Buffer Register for later use.

## SPI Registers

The SPI interface uses the following registers:

* **SPCR** (SPI Control Register): This register controls the SPI interface.
* **SPSR** (SPI Status Register): This register contains the SPI status flags.
* **SPDR** (SPI Data Register): This register contains the SPI data.

### SPCR (SPI Control Register)

The SPI Control Register, SPCR, controls the SPI interface. It is located at address 0x2D in the AVR microcontroller.

| Bit | Name | Description |
| --- | ---- | ----------- |
| 7 | SPIE | SPI Interrupt Enable |
| 6 | SPE | SPI Enable |
| 5 | DORD | Data Order |
| 4 | MSTR | Master/Slave Select |
| 3 | CPOL | Clock Polarity |
| 2 | CPHA | Clock Phase |
| 1, 0 | SPR1:0 | Clock Rate Select 1 and 0 |

#### SPIE (SPI Interrupt Enable)

The SPI Interrupt Enable bit, SPIE, enables the SPI interrupt. When this bit is written to one, and the SPI interrupt flag, SPIF, in SPSR is set, the SPI interrupt is executed. The SPI interrupt is executed at the end of a SPI serial transfer.

#### SPE (SPI Enable)

The SPI Enable bit, SPE, enables the SPI interface. When this bit is written to one, and the SPI interface is configured as a Master, the SPI interface is enabled and the SPI Master will start the serial transfer. When this bit is written to one, and the SPI interface is configured as a Slave, the SPI interface is enabled and the SPI Slave will start the serial transfer when the SS pin is pulled low.

#### DORD (Data Order)

The Data Order bit, DORD, controls the data order in which the data is shifted out and in. When this bit is written to zero, the data is shifted out and in most significant bit first. When this bit is written to one, the data is shifted out and in least significant bit first.

#### MSTR (Master/Slave Select)

The Master/Slave Select bit, MSTR, selects the SPI interface mode. When this bit is written to zero, the SPI interface is configured as a Slave. When this bit is written to one, the SPI interface is configured as a Master.

#### CPOL (Clock Polarity)

The Clock Polarity bit, CPOL, configures the clock polarity. When this bit is written to zero, the SCK line is low when idle. When this bit is written to one, the SCK line is high when idle.

#### CPHA (Clock Phase)

The Clock Phase bit, CPHA, configures the clock phase. When this bit is written to zero, the data is sampled on the leading edge of the SCK line. When this bit is written to one, the data is sampled on the trailing edge of the SCK line.

#### SPR1:0 (Clock Rate Select 1 and 0)

The Clock Rate Select bits, SPR1:0, configure the SPI clock rate. The SPI clock rate is configured by the following formula:

```
SPI Clock Rate = CPU Clock / (2 * (SPR1:0 + 1))
```

### SPSR (SPI Status Register)

The SPI Status Register, SPSR, contains the SPI status flags. It is located at address 0x2E in the AVR microcontroller.

| Bit | Name | Description |
| --- | ---- | ----------- |
| 7 | SPIF | SPI Interrupt Flag |
| 6 | WCOL | Write Collision Flag |
| 5 | - | - |
| 4 | - | - |
| 3 | - | - |
| 2 | - | - |
| 1 | - | - |
| 0 | - | - |

#### SPIF (SPI Interrupt Flag)

The SPI Interrupt Flag bit, SPIF, is set when the SPI serial transfer is complete. This bit is set by hardware when the SPI serial transfer is complete. This bit is cleared by hardware when the SPI interrupt vector is executed.

#### WCOL (Write Collision Flag)

The Write Collision Flag bit, WCOL, is set when a SPI serial transfer is attempted while the SPI interface is busy. This bit is set by hardware when a SPI serial transfer is attempted while the SPI interface is busy. This bit is cleared by hardware when the SPI interrupt vector is executed.

### SPDR (SPI Data Register)

The SPI Data Register, SPDR, contains the SPI data. It is located at address 0x2F in the AVR microcontroller.

## SPI Data Modes

## SPI Interfacing
