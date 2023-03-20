---
title: DC Circuit Analysis
author: ["M Zaki"]
date: 2021-03-29
keywords: [Electrical Engineering, DC Circuit Analysis]
---

# DC Circuit Analysis

- [DC Circuit Analysis](#dc-circuit-analysis)
  - [Introduction](#introduction)
  - [Kirchhoff's Laws](#kirchhoffs-laws)
    - [KCL](#kcl)
      - [Sample Problem](#sample-problem)
      - [More complicated problem](#more-complicated-problem)
      - [Summary: Steps to solve any problem using KCL](#summary-steps-to-solve-any-problem-using-kcl)
    - [KVL](#kvl)
    - [Thevenin and Norton Equivalent Circuits](#thevenin-and-norton-equivalent-circuits)
    - [Superposition Theorem](#superposition-theorem)
    - [Maximum Power Transfer Theorem](#maximum-power-transfer-theorem)
  - [Summary](#summary)
  - [References](#references)


## Introduction

In this section, we will learn how to analyze DC circuits. We will learn how to find the current and voltage in a circuit using Kirchhoff's laws. We will also learn how to find the power in a circuit.

## Kirchhoff's Laws

Kirchhoff's laws are two laws that describe the behavior of electric circuits. They are named after Gustav Kirchhoff, a German physicist who developed them in the 19th century. The first law (**KVL: Kirchhoff's Voltage Law**) states that the sum of the voltages around a closed loop in a circuit is zero. The second law (**KCL: Kirchoff's Current Law**) states that the sum of the currents entering a node is equal to the sum of the currents leaving that node.

### KCL

KCL states that the sum of the currents entering a node is equal to the sum of the currents leaving that node. This means that the current entering a node is equal to the current leaving that node. This is illustrated in the figure below:

![kcl](https://dwma4bz18k1bd.cloudfront.net/tutorials/Kirchhoff%E2%80%99s-Current-Law.jpg)

**Source:** [Circuit Bread](https://www.circuitbread.com/tutorials/how-to-solve-complicated-circuits-with-kirchhoffs-current-law-kcl)

#### Sample Problem

Analyze in the circuit below:

![sample problem](https://dwma4bz18k1bd.cloudfront.net/tutorials/Kirchhoff%E2%80%99s-Current-Law-Tutorial-Problem-1-Circuit-A.jpg)

Given: $I_1 = 1A$ ` ` $I_2 = 2A$ ` ` $R_1 = 10$ ` ` $R_2 = 20$ ` ` $R_3 = 30$
**Source**: [Circuit Bread](https://www.circuitbread.com/tutorials/how-to-solve-complicated-circuits-with-kirchhoffs-current-law-kcl)

> When we ask to **analyze** a circuit, we are basically trying to know everything about this circuit, basically, find every value that is unknown.

**Analysis:**

1. Review what has been given and what you need. In this problem, we have 3 resistors and their value, 2 currrent sources and their values. We need to find the current in the third resistor, $I_3$. On first look, it doesn't look like we can solve this problem using the practices of solving resistor circuits, so we need to use KCL or (later KVL).

2. Choose a reference ground, if it hasn't already been defined. Standard practice is to choose buttom node as ground. Therefore, node $ N_2 $ is the reference ground.

3. Since we don't know the current flowing throught $ R_3 $, we will use the potential difference across $ R_3 $ to derive an equation for $ I_3 $, which leads to the the following equation:

$$ I_3 = \frac{V_1 - V_2}{R_3} $$

Since we chose $ N_2 $ as the reference ground, then $ V_2 = 0 $:

$$ I_3 = \frac{V_1}{R_3} $$

$$ I_3 = \frac{V_1}{30} \space \space eq(1) $$ 

4. Now, we will use KCL to derive another equation for $ I_3 $ because we have 2 unknowns, so we need 2 equations:

$$ I_3 = I_1 + I_2 $$

$$ I_3 = 3 \space \space eq(2) $$

> **Note:** We assumed the direction of unknown current to be towards $ N_2 $ till we are proven if we're right or wrong after we do the math.

5. Now, we will substitute $ I_3 $ from equation (1) into equation (2):

$$ \frac{V_1}{30} = 3 $$
$$ V_1 = 90 $$

#### More complicated problem

<!-- TODO solve a more complicated problem -->

#### Summary: Steps to solve any problem using KCL

<!-- FIXME potentially missing steps -->

1. Review what has been given and what you need.

2. Choose a reference ground, if it hasn't already been defined.

3. Use the potential difference across the unknown resistor(s) to derive an equation for the unknown current.

4. Use KCL to derive another equation for the unknown current.

5. Solve the derived equations to find the unknown values.

### KVL

<!-- TODO -->

### Thevenin and Norton Equivalent Circuits

<!-- TODO -->

### Superposition Theorem

<!-- TODO -->

### Maximum Power Transfer Theorem

<!-- TODO -->

## Summary

<!-- TODO -->

## References

- [Circuit Bread](https://www.circuitbread.com/tutorials/)

- 