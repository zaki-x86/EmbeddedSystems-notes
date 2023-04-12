# Voltage, Power, Current and Energy

**Table of Contents**

* Power vs. Energy
  * Batteries vs Capacitors
* Ohm's Law
* Resistivity
* Conductivity
* Summary
* References

Imagine you have a water tank that is sitting on a tall platform, just like a lake sitting on top of a hill. The water in the tank is similar to the voltage in an electrical circuit. The higher the water level in the tank, the higher the voltage in the circuit.

Now, let's assume there is a pipe connected to the bottom of the tank, which represents the wire in the electrical circuit. The flow of water through the pipe is similar to the current in the electrical circuit.

The size of the pipe is like the resistance in an electrical circuit. The bigger the pipe, the less resistance to the flow of water, and the higher the water flow through the pipe. Similarly, the lower the resistance in an electrical circuit, the higher the current flow through the circuit.

If we want to increase the water flow through the pipe, we have two options: either increase the height of the water in the tank (voltage) or increase the size of the pipe (decrease resistance). Similarly, in an electrical circuit, we can increase the current flow by increasing the voltage or decreasing the resistance.

Potential difference is the amount of energy required to move a unit charge from one point to another. The unit of potential difference is the volt (V). The volt is defined as the potential difference between two points that will cause a current of 1 ampere when a resistance of 1 ohm is connected between them. When we talk about voltage, we’re talking about the electric potential between two points in relation to each other. We typically assume that the lowest point is “0” or what we call “ground” as a reference. But then sometimes you get negative voltages, which just means that the electric potential at that point is below what we established as our “ground” potential.

### Power vs. Energy

We know from school that the difference between power and energy is only a matter of time component, which is unsatisfying and doesn't tell much. You can think of energy as the amount of effort a person uses to climb the stairs, while power is the rate at which they are climbing.

Imagine two people, Alice and Bob, both climb a flight of stairs with the same height. Alice takes her time, and it takes her 10 seconds to climb the stairs. Bob, on the other hand, is in a hurry and climbs the same stairs in just 5 seconds. Both Alice and Bob used the same amount of energy to climb the stairs, as the height of the stairs is the same for both of them. However, Bob had to exert twice as much power as Alice to climb the stairs in half the time.

In this analogy, the height of the stairs is equivalent to the energy consumed, while the time it takes to climb the stairs is equivalent to the power expended. The energy is a measure of the amount of work done, while power is a measure of how quickly that work is done. So, while Alice and Bob both exerted the same amount of energy, Bob had a higher power output because he was able to complete the task in less time.

We usually work with power and disregard energy, but when we work with energy storage devices such as batteries and capacitor, we will need to understand the distinction between power and energy.

#### Batteries vs Capacitors

Batteries and capacitors are both energy storage devices. They both store energy, but they do it in different ways. Batteries store energy in the form of chemical reactions, while capacitors store energy in the form of electric fields.

Let's imagine a water tank and a water balloon. The tank is like a battery, it can store a large amount of water (energy) but it takes some time to fill and empty. On the other hand, the water balloon is like a capacitor, it can't hold as much water (energy) as the tank, but it can be filled and emptied very quickly. So, the tank has a high energy density, but a low power density, while the water balloon has a low energy density, but a high power density. Similarly, batteries have a higher energy density, meaning they can store more energy per unit volume or weight, but they have a lower power density, meaning they can't release the stored energy as quickly as capacitors. Capacitors, on the other hand, have a lower energy density, but a higher power density, meaning they can release their stored energy very quickly, making them suitable for applications that require bursts of energy, such as camera flashes or electric vehicles.

Mathematically speaking, electric power is current times voltage, or the rate of energy transfer per unit time. The unit of power is the watt (W). The watt is defined as the power required to dissipate 1 joule of energy per second. The joule is the unit of energy, and it is defined as the amount of energy required to move a charge of 1 coulomb through a potential difference of 1 volt.

### Ohm's Law

![](https://dwma4bz18k1bd.cloudfront.net/tutorials/CircuitBread-Ohms-Law-Animation.gif) source: [Circuit Bread](https://www.circuitbread.com/)

Ohm's law is a fundamental law of electrical engineering that states that the current through a conductor between two points is directly proportional to the potential difference across the two points. It is usually stated as:

$$I = \frac{V}{R}$$

or

$$V = IR$$

Where I is the current in amperes, V is the potential difference in volts, and R is the resistance in ohms. The constant of proportionality is the resistance of the conductor.

### Resistivity

The resistivity of a material is a measure of how strongly it opposes the flow of electric current. The unit of resistivity is the ohm-meter (Ωm). The ohm-meter is defined as the resistance of a conductor of 1 meter length in which a current of 1 ampere flows when a potential difference of 1 volt is applied.

$$R = \rho \frac{l}{A} (\Omega)$$

Where R is the resistance, ρ is the resistivity, l is the length of the conductor, and A is the cross-sectional area of the conductor.

### Conductivity

The conductivity of a material is a measure of how easily it allows the flow of electric current. The unit of conductivity is the siemens per meter (S/m). The siemens per meter is defined as the reciprocal of the resistance of a conductor of 1 meter length in which a current of 1 ampere flows when a potential difference of 1 volt is applied.

$$G = \frac{I}{V} Siemens(S)$$

Where G is the conductivity measured in Siemens.

### Summary

In this tutorial, we learned about the basic concepts of electricity and electrical circuits. We learned about the basic units of electricity, such as voltage, current, resistance, power, and energy. We also learned about Ohm's law, which states that the current through a conductor between two points is directly proportional to the potential difference across the two points. We also learned about resistivity and conductivity, which are measures of how strongly a material opposes or allows the flow of electric current.

### References

* [Ohm's Law](https://en.wikipedia.org/wiki/Ohm's\_law)
* [Resistivity](https://en.wikipedia.org/wiki/Resistivity)
* [Conductivity](https://en.wikipedia.org/wiki/Conductivity)
* [Electric Potential](https://en.wikipedia.org/wiki/Electric\_potential)
* [Electric Power](https://en.wikipedia.org/wiki/Electric\_power)
* [Electric Energy](https://en.wikipedia.org/wiki/Electric\_energy)

***

**Next** : Branchs, nodes and loops
