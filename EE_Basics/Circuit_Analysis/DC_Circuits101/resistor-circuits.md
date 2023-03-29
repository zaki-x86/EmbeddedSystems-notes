---
title: Resistor Circuits
author: ["M Zaki"]
date: 2020-05-01
keywords: ["Electrical Engineering", "Resistor Circuits"]
---

# Resistor Circuits

- [Resistor Circuits](#resistor-circuits)
  - [Introduction](#introduction)
  - [Resistors in Series](#resistors-in-series)
  - [Resistors in Parallel](#resistors-in-parallel)
  - [Delta vs Wye Resistance Configuration](#delta-vs-wye-resistance-configuration)
    - [Why is it important to know the difference between Delta and Wye configurations?](#why-is-it-important-to-know-the-difference-between-delta-and-wye-configurations)
    - [Transformation from Delta to Wye](#transformation-from-delta-to-wye)
  - [Divider Circuits](#divider-circuits)
  - [Voltage Divider](#voltage-divider)
  - [Current Divider](#current-divider)
  - [Wheatstone Bridge](#wheatstone-bridge)
  - [Analyzing a resistor circuit with two batteries](#analyzing-a-resistor-circuit-with-two-batteries)
  - [Summary](#summary)

## Introduction

A resistor is a passive two-terminal electrical component that implements electrical resistance as a circuit element. In electronic circuits, resistors are used to reduce current flow, adjust signal levels, to divide voltages, bias active elements, and terminate transmission lines, among other uses. The resistor is a fundamental component of electronic circuits, and is used in virtually all electronic equipment.

## Resistors in Series

In a series circuit, the same current flows through each resistor. The total resistance of the circuit is the sum of the individual resistances. The total voltage drop across the circuit is the same across each resistor.

![]()

## Resistors in Parallel

In a parallel circuit, the voltage drop across each resistor is the same. The total current through the circuit is the sum of the individual currents through each resistor. The total resistance of the circuit is the reciprocal of the sum of the reciprocals of the individual resistances.

![]()

## Delta vs Wye Resistance Configuration

In a Delta configuration, the resistors are connected in a triangle shape. Each resistor has one end connected to the end of another resistor and the other end connected to the next resistor. The three points where the resistors meet are the nodes of the circuit.

![Delta Configuration](https://uploads-cdn.omnicalculator.com/images/delta_to_wye/delta.png?width=425&enlarge=0&format=webp)

**Source:** [Omni Calculator](https://www.omnicalculator.com/physics/)

In a Wye configuration, the resistors are connected in a Y shape. Each resistor has one end connected to a common point, and the other end connected to a separate point. The three separate points are the nodes of the circuit.

![Wye Configuration](https://uploads-cdn.omnicalculator.com/images/delta_to_wye/wye.png?width=425&enlarge=0&format=webp)

**Source:** [Omni Calculator](https://www.omnicalculator.com/physics/)

The configuration can be re-drawn to look like this:
![Delta and Wye Configurations](https://cdn.kastatic.org/ka-perseus-images/a88345766c62854d2c426c1c8f034f3ca7767e01.svg)

**Source:** [Khan Academy](https://www.khanacademy.org/science/electrical-engineering/ee-circuit-analysis-topic/ee-resistor-circuits/a/ee-delta-wye-resistor-networks)

### Why is it important to know the difference between Delta and Wye configurations?

These two configuration often occurs during circuit simplification, knowing about them helps to avoid getting stuck when you identify them in circuit analysis.

### Transformation from Delta to Wye

<!-- TODO -->


## Divider Circuits

A divider circuit is a circuit that divides the voltage of a source between two or more resistors. The total resistance of the circuit is the sum of the individual resistances. The total current through the circuit is the same across each resistor.

![]()

<!-- TODO -->

## Voltage Divider

A voltage divider is a circuit that divides the voltage of a source between two resistors. The total resistance of the circuit is the sum of the individual resistances. The total current through the circuit is the same across each resistor.

![]()

$$ V_{out} = \frac{R_2}{R_1 + R_2} V_{in} $$

## Current Divider

A current divider is a circuit that divides the current of a source between two resistors. The total resistance of the circuit is the sum of the individual resistances. The total voltage drop across the circuit is the same across each resistor.

![]()

$$ I_{out} = \frac{R_1}{R_1 + R_2} I_{in} $$

## Wheatstone Bridge

The Wheatstone bridge is a circuit that is used to measure the unknown resistance of a resistor. The bridge is made up of four resistors, two of which are unknown. The bridge is balanced when the voltage across the two unknown resistors is zero. The bridge is unbalanced when the voltage across the two unknown resistors is not zero.

![]()

<!-- TODO -->

$$ R_1 = \frac{R_2 R_3}{R_4} $$

## Analyzing a resistor circuit with two batteries

![]()

<!-- TODO -->

## Summary

- Resistors in series have the same current flowing through them.
- Resistors in parallel have the same voltage drop across them.
- Delta and Wye configurations are used to simplify circuits.
- Divider circuits divide the voltage or current of a source between two or more resistors.
- Voltage dividers divide the voltage of a source between two resistors.
- Current dividers divide the current of a source between two resistors.
- The Wheatstone bridge is used to measure the unknown resistance of a resistor. The bridge is balanced when the voltage across the two unknown resistors is zero.

---

**Next**: [DC Circuit Analysis](./dc-circuit-analysis.md)
