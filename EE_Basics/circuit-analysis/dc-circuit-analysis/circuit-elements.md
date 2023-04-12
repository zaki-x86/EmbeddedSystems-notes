---
description: Basic elements of any DC circuit
---

# Circuit Elements

## Circuit Elements

**Table of Contents**

* Active Elements vs Passive Elements
* Voltage Sources
* Current Sources
* Dependent Sources
* Non-ideal power sources
* Passive Sign Convention
* Summary
* References

### Active Elements vs Passive Elements

A circuit element is a component that is used to build a circuit. There are two types of circuit elements: active elements and passive elements.

An active element is a circuit element that can produce an output signal that is different from its input signal. Examples of active elements are transistors, operational amplifiers, and power supplies.

A passive element is a circuit element that can only pass an input signal without modifying it. Examples of passive elements are resistors, capacitors, and inductors.

In terms of energy, active elements consume energy and produce energy. Passive elements only consume energy or (store/release) energy.

Transistors, operational amplifiers, power supplies are active elements while resistors, capacitors, inductors are passive elements.

### Voltage Sources

A voltage source is a circuit element that produces a voltage. It is an active element that can produce an output signal that is different from its input signal. It it is represented in a circuit with these symbols:

![](https://dwma4bz18k1bd.cloudfront.net/tutorials/Voltage-Sources-Schematic-Symbol.jpg)

source: [Circuit Bread](https://www.circuitbread.com/)

The voltage source is connected to two terminals. The terminal that is connected to the positive side of the voltage source is called the positive terminal. The terminal that is connected to the negative side of the voltage source is called the negative terminal.

An ideal voltage source is a voltage source that produces a constant voltage and will produce or consume any amount of current to keep the voltage constant. If there is no resistance in the circuit, the voltage source will produce an infinite amount of current, meaning that postive and negative terminals will be shorted together, effectively leading to an infinite amount of current which leads to damage of the circuit. To prevent this, a resistor is connected in series with the voltage source.

The situation in which a power source is connected in a circuit with no resistance is known as **short circuit**.

### Current Sources

A current source is a circuit element that produces a constant amount of current across its terminals by varying its voltage.

You may never see a current source in a circuit. It is not used in practice. It is only used in theory to model other elements that produce the typical behavior of altering voltage to maintain a rated current.

### Dependent Sources

In electrical circuit theory, dependent sources are voltage or current sources whose values are determined by the voltage or current in some other part of the circuit. A dependent source can be thought of as a "slave" to some other circuit variable.

There are two types of dependent sources: voltage-controlled dependent sources and current-controlled dependent sources.

A voltage-controlled dependent source (VCCS) is a dependent source in which the source current is proportional to the voltage across a different part of the circuit. Mathematically, a VCCS is expressed as:

$$I_s = \alpha V_{in}$$

where $I\_s$ is the source current, $\alpha$ is the proportionality constant, and $V\_{in}$ is the voltage across the input terminals of the VCCS.

A current-controlled dependent source (CCCS) is a dependent source in which the source voltage is proportional to the current through a different part of the circuit. Mathematically, a CCCS is expressed as:

$$V_s = \alpha I_{in}$$

where $V\_s$ is the source voltage, $\alpha$ is the proportionality constant, and $I\_{in}$ is the current through the input terminals of the CCCS.

Dependent sources are used in circuit analysis to model various types of circuits and devices. They are particularly useful for modeling amplifiers, operational amplifiers, and transistors

### Non-ideal power sources

In real life, power sources are not ideal. They have some limitations. They are not perfect. They have some imperfections. They are not perfect voltage sources or perfect current sources. They are non-ideal power sources.

In an ideal power source, the voltage or current remains constant regardless of the load or the environment, but in the case of non-ideal sources, the voltage or current can vary depending on different factors.

**Batteries**: Batteries have an internal resistance that causes a voltage drop when current flows through them. As a result, the voltage output of a battery may vary depending on the load and the age of the battery.

Sometimes we model batteries as ideal voltage sources. In this case, we assume that the voltage output of the battery is constant regardless of the load. This is a good approximation for small loads. However, this approximation is not valid for large loads.

### Passive Sign Convention

The passive sign convention is a convention that is used to determine the sign of the voltage and current in a circuit. It is used to determine the direction of the current and the direction of the voltage.

The Passive Sign Convention dictates that for passive components such as resistors, the current flows from the positive terminal to the negative terminal, i.e., the arrow representing the current should point towards the negative terminal. For capacitors and inductors, the current direction is determined by the change in voltage across them. If the voltage across a capacitor is increasing, the current flows into the positive terminal of the capacitor, and if the voltage is decreasing, the current flows out of the positive terminal. For inductors, the current flows into the positive terminal when the magnetic field is expanding, and it flows out of the positive terminal when the magnetic field is collapsing.

For voltage sources, the positive terminal is denoted by a longer line or a plus sign, and the negative terminal is denoted by a shorter line or a minus sign. The direction of the current through the voltage source is determined by the polarity of the voltage source with respect to the rest of the circuit.

For current sources, the direction of the current is denoted by an arrow, and the polarity of the voltage across the current source is determined by the direction of the current with respect to the rest of the circuit.

![active component](https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/Electric\_power\_source\_animation.gif/150px-Electric\_power\_source\_animation.gif) power source (active component)

![passive component](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Electric\_load\_animation.gif/150px-Electric\_load\_animation.gif) passive component

source: [Wikipedia](https://en.wikipedia.org/wiki/Passive\_sign\_convention)

### Summary

In this tutorial, we learned about the following:

* Active elements vs passive elements
* Voltage sources
* Current sources
* Dependent sources
* Non-ideal power sources
* Passive sign convention

### References

* [Voltage Source](https://en.wikipedia.org/wiki/Voltage\_source)
* [Current Source](https://en.wikipedia.org/wiki/Current\_source)
* [Dependent Source](https://en.wikipedia.org/wiki/Dependent\_source)
* [Non-ideal Power Sources](https://en.wikipedia.org/wiki/Non-ideal\_power\_source)
* [Passive Sign Convention](https://en.wikipedia.org/wiki/Passive\_sign\_convention)

***

**Next**: Resistor Circuits
