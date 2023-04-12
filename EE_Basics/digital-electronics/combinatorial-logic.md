# Combinatorial Logic

Combinatorial logic is that whose state always reflects the inputs. There’s no memory; past events have no impact on present outputs.

The easiest way to understand how any combinatorial circuit works—be it a single component or a hundred interconnected ICs is via a _**truth table**_, a matrix that defines every possible combination of inputs and outputs.

Combinatorial logic is a fundamental concept in digital electronics that involves the implementation of logic circuits to perform logical operations on input signals to generate output signals. Combinatorial logic circuits use boolean logic, which is a form of algebra that deals with binary variables and logic operations. In this tutorial, we will discuss the basics of combinatorial logic, its components, and the various types of combinatorial logic circuits.

Logic gates are the building blocks of combinatorial logic. Most are derived from the _**AND**_, _**OR**_, and _**NOT**_ gates. The _**NAND**_ and _**NOR**_ gates are also useful.

### Logic Gates

#### AND Gate

The _**AND**_ gate is a logic gate that outputs a 1 only when all of its inputs are 1.

Here is the truth table for the AND gate:

| A | B | A AND B |
| - | - | ------- |
| 0 | 0 | 0       |
| 0 | 1 | 0       |
| 1 | 0 | 0       |
| 1 | 1 | 1       |

#### OR Gate

The _**OR**_ gate is a logic gate that outputs a 1 when at least one of its inputs is 1.

Here is the truth table for the OR gate:

| A | B | A OR B |
| - | - | ------ |
| 0 | 0 | 0      |
| 0 | 1 | 1      |
| 1 | 0 | 1      |
| 1 | 1 | 1      |

#### NOT Gate

The _**NOT**_ gate is a logic gate that outputs the opposite of its input.

Here is the truth table for the NOT gate:

| A | NOT A |
| - | ----- |
| 0 | 1     |
| 1 | 0     |

#### NAND Gate

The _**NAND**_ gate is a logic gate that outputs the opposite of the AND gate.

Here is the truth table for the NAND gate:

| A | B | A NAND B |
| - | - | -------- |
| 0 | 0 | 1        |
| 0 | 1 | 1        |
| 1 | 0 | 1        |
| 1 | 1 | 0        |

#### NOR Gate

The _**NOR**_ gate is a logic gate that outputs the opposite of the OR gate.

Here is the truth table for the NOR gate:

| A | B | A NOR B |
| - | - | ------- |
| 0 | 0 | 1       |
| 0 | 1 | 0       |
| 1 | 0 | 0       |
| 1 | 1 | 0       |

#### XOR Gate

The _**XOR**_ gate is a logic gate that outputs a 1 when its inputs are different.

Here is the truth table for the XOR gate:

| A | B | A XOR B |
| - | - | ------- |
| 0 | 0 | 0       |
| 0 | 1 | 1       |
| 1 | 0 | 1       |
| 1 | 1 | 0       |

#### XNOR Gate

The _**XNOR**_ gate is a logic gate that outputs a 1 when its inputs are the same.

Here is the truth table for the XNOR gate:

| A | B | A XNOR B |
| - | - | -------- |
| 0 | 0 | 1        |
| 0 | 1 | 0        |
| 1 | 0 | 0        |
| 1 | 1 | 1        |

### Boolean Algebra

Boolean algebra is a branch of algebra in which the values of the variables are the truth values _**true**_ and _**false**_, usually denoted 1 and 0 respectively. Instead of elementary algebra where the values of the variables are numbers and the main operations are addition and multiplication, the main operations of Boolean algebra are the conjunction (_**AND**_), the disjunction (_**OR**_), and the negation (_**NOT**_).

#### Boolean Functions

A Boolean function is a function that takes Boolean values as inputs and returns a Boolean value as output. A Boolean function can be represented by a truth table, which lists the output value of the function for each possible combination of input values.

#### Boolean Algebra Laws

These laws are used to simplify Boolean expressions.

**De Morgan's Theorem**

De Morgan's theorem states that the following are equivalent:

* $$\overline{A \land B} = \overline{A} \lor \overline{B}$$
* $$\overline{A} \land \overline{B} = \overline{A \lor B}$$

**Double Complement**

The double complement theorem states that the following are equivalent:

* $$\overline{\overline{A}} = A$$

**Idempotent Law**

The idempotent law states that the following are equivalent:

* $$A \land A = A$$
* $$A \lor A = A$$

**Absorption Law**

The absorption law states that the following are equivalent:

* $$A \land 0 = 0$$
* $$A \land 1 = A$$
* $$A \lor 0 = A$$
* $$A \lor 1 = 1$$

**Commutative Law**

The commutative law states that the following are equivalent:

* $$A \land B = B \land A$$
* $$A \lor B = B \lor A$$

**Associative Law**

The associative law states that the following are equivalent:

* $$A \land (B \land C) = (A \land B) \land C$$
* $$A \lor (B \lor C) = (A \lor B) \lor C$$

**Distributive Law**

The distributive law states that the following are equivalent:

* $$A \land (B \lor C) = (A \land B) \lor (A \land C)$$
* $$A \lor (B \land C) = (A \lor B) \land (A \lor C)$$

**Identity Law**

The identity law states that the following are equivalent:

* $$A \land 0 = 0$$
* $$A \lor 1 = 1$$

### Combinatorial Logic Circuits

Combinatorial logic circuits are circuits that have no memory. They are used to perform logical operations on a set of inputs and produce a set of outputs. The outputs are determined by the inputs and the logic gates used in the circuit.

#### Half Adder

The half adder is a combinational logic circuit that performs addition on two bits. It has two inputs, _**A**_ and _**B**_, and two outputs, _**S**_ and _**C**_. The _**S**_ output is the sum of the two inputs, while the _**C**_ output is the carry bit.

Here is the truth table for the half adder:

| A | B | S | C |
| - | - | - | - |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

#### Full Adder

The full adder is a combinational logic circuit that performs addition on three bits. It has three inputs, _**A**_, _**B**_, and _**C**_, and two outputs, _**S**_ and _**C**_. The _**S**_ output is the sum of the three inputs, while the _**C**_ output is the carry bit.

Here is the truth table for the full adder:

| A | B | C | S | C |
| - | - | - | - | - |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

#### Multiplexer

#### Demultiplexer

#### Decoder

#### Encoder

#### Priority Encoder
