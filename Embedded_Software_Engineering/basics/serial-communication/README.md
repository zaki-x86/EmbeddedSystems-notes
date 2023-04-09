# Communication Protocols

**What is communication?**
it is the process of exchanging data between two or more devices.
Communication between devices in a system is a critical part of embedded software development. There are many different ways to communicate between devices, and each method has its own advantages and disadvantages.

Digital data can be transferred between two devices either in serial or in parallel. When we studied IO interfacing, we used parallel communication primarly to communicate between the microcontroller and the external devices such that each pin of the microcontroller is connected to a pin of the external device to transfer a single bit of data.

In this section, we will learn about serial communication and how it is used to communicate between devices. First, let's know the difference between parallel and serial communication.

![illustration of serial vs parallel communication](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9d/Serial_and_Parallel_Data_Transmission.svg/300px-Serial_and_Parallel_Data_Transmission.svg.png)

**Parallel Communication**
In parallel communication, multiple bits of data are sent at the same time. This is done by sending multiple wires. Each wire carries a single bit of data. This is shown in the diagram below.

This form of communication has its own advantanges and disadvantages. The main advantage of parallel communication is that it is faster than serial communication and quite easy to setup. The main disadvantage of parallel communication is that it requires more wires than serial communication, therefore, it is costly and is not really practical when developing complex systems or when trying to communicate with other devices over long distances.

**Serial Communication**
Serial communication is the process of sending data one bit at a time, sequentially, over a communication channel or computer bus. This is in contrast to parallel communication, where several bits are sent as a whole, on a link with several parallel channels.

The main advantage of serial communication is that it is cheaper than parallel communication since we try to achieve the communication between two or more devices via very few wires, typically use only one or two wires to send and receive data. The main disadvantage of serial communication is that it is slower than parallel communication and can be a bit more complicated to setup.

## Serial Communication Protocols

In this introductory section, we will establish a framework in mind for what makes a serial communication, later on will go in depth into different architectures.

Serial communication protocols are used to define how data is sent and received between devices. There are many different serial communication protocols, but the most common ones are: USART, SPI, and I2C.

Serial communication protocol architecture typically has the following characteristics:

### Asynchronous or synchronous

Asynchronous communication is a method of transmitting data where data is transmitted without any fixed timing between the transmitter and receiver. In this type of communication, each data byte is transmitted as a series of bits, with start and stop bits framing each byte. The start bit tells the receiver that a new byte is coming, and the stop bit indicates the end of the byte. The sender and receiver don't need to be synchronized with a common clock signal. Asynchronous communication is commonly used for low-speed communication and short distances. Examples of asynchronous protocols include UART, RS-232.

On the other hand, synchronous communication is a method of transmitting data where data is transmitted with a fixed timing between the transmitter and receiver. In this type of communication, the sender and receiver are synchronized with a common clock signal. The clock signal is used to indicate when data can be transmitted and when it should be received. This ensures that the sender and receiver are in sync and that data is transmitted and received at the same rate. Synchronous communication is commonly used for high-speed communication and long distances. Examples of synchronous protocols include SPI and I2C.

#### Note

Bits are sent in the form of a square wave, such that each bit has a duration, In asynchronous communication, the transmitter and receiver must agree on the timing of each bit. To achieve this, they use a fixed baud rate that determines the time between consecutive bits. The baud rate is usually specified in bits per second (bps), and it determines the duration of each bit.

At the beginning of each byte, the transmitter sends a start bit that is always low, followed by the data bits, and then a stop bit that is always high. The receiver detects the start bit and then samples the incoming data at regular intervals based on the baud rate to determine the values of each data bit.

### Master/Slave

Serial communication can be either master/slave or peer-to-peer. In a master/slave configuration, the master device initiates communication and the slave device responds. In peer-to-peer communication, there is no master or slave, and any device can initiate communication.

### Simplex / Half-duplex (HDX) / Full-duplex (FDX)

In simplex communication, data can only be transmitted in one direction. In half-duplex communication, data can be transmitted in both directions, but only one direction at a time. In full-duplex communication, data can be transmitted in both directions at the same time.

### Speed

Serial communication protocols can be categorized by their speed. The speed of a serial communication protocol is determined by the baud rate, which is the number of bits transmitted per second. The baud rate is usually specified in bits per second (bps), and it determines the duration of each bit.

### Error detection

Serial communication often includes error detection and correction mechanisms such as checksums, CRCs, or parity bits to ensure that data is transmitted accurately.

### Hardware Interface

Serial communication typically requires a specific hardware interface to be implemented. As it is tedious or to complex to do it in software.