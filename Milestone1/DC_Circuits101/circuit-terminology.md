---
title: Branches, nodes and loops in an electric circuit
Author: ["M Zaki"]
Date: 2019-09-01
Keywords: [Electrical Engineering, Circuit terminology]
---

# Circuit Terminology

- [Circuit Terminology](#circuit-terminology)
  - [Series and parallel branches](#series-and-parallel-branches)
  - [Summary](#summary)

Aa branch is a single path for the flow of electric current. It can be a simple wire or a more complex series of interconnected components. It can be thought of as a generic term that represents a signle element in a circuit that has two terminals.

A node is a point where two or more branches meet. A good way to think of it may be a junction where currents are flowing in and out depending on the different branches.

A loop is a path that starts and ends at the same node.

![](https://dwma4bz18k1bd.cloudfront.net/tutorials/Circuit-Nodes-Example.jpg)

![](https://dwma4bz18k1bd.cloudfront.net/tutorials/Circuit-Loops-Example.jpg)

## Series and parallel branches

A series branch is a branch where the current flows in a single direction. The current in a series branch is the same at all points along the branch. The voltage across the branch is the same at all points along the branch.

A parallel branch is a branch where the current splits into two or more paths. The current in a parallel branch is the same at all points along the branch. The voltage across the branch is the same at all points along the branch.

![](https://dwma4bz18k1bd.cloudfront.net/tutorials/Series-Parallel-Components-Current.jpg)

For branches to be in paraller, they must be connected at a single node.

![](https://dwma4bz18k1bd.cloudfront.net/tutorials/Parallel-Branches-Nodes.jpg)

Series branches share the same current. Parallel branches share the same voltage.

The reason you would be interested in series parallel connections is primarly to simplify the circuit. If you have a circuit with a lot of branches, you can simplify it by combining some of the branches into series or parallel branches.

To simplify series resistors, add the resistances together. However, to simplify parallel resistors, you must use the reciprocal of the sum of the reciprocals of the resistances.

$$ R_{total} = \frac{1}{\frac{1}{R_1} + \frac{1}{R_2} + .. + \frac{1}{R_n}} $$

or 

$$ \frac{1}{R_{total}} = \frac{1}{R_1} + \frac{1}{R_2} + ... + \frac{1}{R_n} $$

In case you only have two resistors in parallel, you can use the following formula:

$$ R_1 || R_2 = R_{total} = \frac{R_1 R_2}{R_1 + R_2} $$

## Summary

* A branch is a single path for the flow of electric current.
* A node is a point where two or more branches meet.
* A loop is a path that starts and ends at the same node.
* A series branch is a branch where the current flows in a single direction.
* A parallel branch is a branch where the current splits into two or more paths.
* Series branches share the same current.
* Parallel branches share the same voltage.
* To simplify series resistors, add the resistances together.
* To simplify parallel resistors, you must use the reciprocal of the sum of the reciprocals of the resistances.

---

**Next** : [Circuit Elements](./circuit-elements.md)