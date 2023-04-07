# Bitwise Operations

### Introduction

Bitwise operations are essential operations used in computer science, especially in low-level programming languages like C. Bitwise operators enable us to manipulate the individual bits of a binary number, which is useful in many different contexts, including low-level system programming, data compression, cryptography, and graphics programming. In this tutorial, we will discuss bitwise operators in C, their usage, and some of the common applications of these operations.

### Bitwise Operators

C provides six bitwise operators on `int` and `char` types. These operators are:

* `&` (bitwise AND)
* `|` (bitwise OR)
* `^` (bitwise XOR)
* `~` (bitwise NOT)
* `<<` (left shift)
* `>>` (right shift)

In the following sections, we will discuss each of these operators in detail.

#### Bitwise AND

The bitwise AND operator `&` is a binary operator that takes two operands and performs the bitwise AND operation on each pair of corresponding bits of the two operands.

```C
int a = 5; //  0000 0101
int b = 7; // 0000 0111
int c = a & b; // 0000 0101
```

#### Bitwise OR

The bitwise OR operator `|` is a binary operator that takes two operands and performs the bitwise OR operation on each pair of corresponding bits of the two operands.

```C
int a = 5; // 0000 0101
int b = 7; // 0000 0111
int c = a | b; // 0000 0111
```

#### Bitwise XOR

The bitwise XOR operator `^` is a binary operator that takes two operands and performs the bitwise XOR operation on each pair of corresponding bits of the two operands.

```C
int a = 5; // 0000 0101
int b = 7; // 0000 0111
int c = a ^ b; // 0000 0010
```

#### Bitwise NOT

The bitwise NOT operator `~` is a unary operator that takes one operand and performs the bitwise NOT operation on each bit of the operand.

```C
int a = 5; // 0000 0101
int b = ~a; // 1111 1010
```

#### Left Shift

The left shift operator `<<` is a binary operator that takes two operands. The first operand is the value to be shifted, and the second operand is the number of bits to shift the first operand to the left. The left shift operator shifts the bits of the first operand to the left by the number of bits specified by the second operand. The bits shifted out of the left side of the operand are discarded. The bits shifted in on the right side of the operand are filled with zeros.

```C
int a = 5; // 0000 0101
int b = a << 1; // 0000 1010

int x = 1; // 0000 0001
int y = x << 3; // 0000 1000
```

#### Right Shift

The right shift operator `>>` is a binary operator that takes two operands. The first operand is the value to be shifted, and the second operand is the number of bits to shift the first operand to the right. The right shift operator shifts the bits of the first operand to the right by the number of bits specified by the second operand. The bits shifted out of the right side of the operand are discarded. The bits shifted in on the left side of the operand are filled with zeros.

```C
int a = 5; // 0000 0101
int b = a >> 1; // 0000 0010

int x = 8; // 0000 1000
int y = x >> 2; // 0000 0010
```

### Notes

* Bitwise operators can only be applied to positive integers, otherwise, undefined behavior will occur.
* The `OR` operator can be used to calculate the sum of two numbers without using the `+` operator.

```C
int a = 5;      // 5(0b00000101)
int b = 7;      // 7(0b00000111)
int c = a | b;  // 12(0b00001100)
```

* The `AND` operator can be used to check if a number is even or odd.

```C
int a0 = 5;      // 5(0b00000101)
int a1 = 6;      // 6(0b00000110)
int b0 = a0 & 1;  // 1(0b00000001)
int b1 = a1 & 1;  // 0(0b00000000)

if (b == 0) {
    printf("a is even\n");
} else {
    printf("a is odd\n");
}
```

* The `XOR` operator is the most useful operator from a technical perspective, it can be used in the following:

1. To swap two numbers without using a temporary variable.

```C
int a = 5; // 5(0b00000101)
int b = 7; // 7(0b00000111)

a = a ^ b; // 2(0b00000010)
b = a ^ b; // 5(0b00000101)
a = a ^ b; // 7(0b00000111)
```

2. To check if two numbers are equal without using the `==` operator.

```C
int a0 = 5; // 5(0b00000101)
int a1 = 6; // 6(0b00000110)
int b0 = 7; // 7(0b00000111)
int b1 = 6; // 7(0b00000111)
int c0 = a0 ^ b0; // 2(0b00000010)
int c1 = a1 ^ b1; // 0(0b00000000)

// c_i == 0 means a_i == b_i
```

There are a lot of hacks and tricks that can be done using bitwise operators, but we will not discuss them in this tutorial. If you are interested in learning more about bitwise operations, you can check out the following resources:

* [Bitwise Tricks For Competitive Programming](https://www.geeksforgeeks.org/bit-tricks-competitive-programming/)
* [Bitwise Hacks](https://www.geeksforgeeks.org/bitwise-hacks-for-competitive-programming/)

### Bitwise operators in Embedded Systems Programming

In embedded systems, we often wish to perform operations on a single bit of a register. For example, we may wish to set a bit in a register to 1, or clear a bit in a register to 0. In this case, we can use bitwise operators to perform these operations.

```C
// Set bit 0 of register A to 1
A |= (1 << 0);

// Clear bit 0 of register A to 0
A &= ~(1 << 0);

// Toggle bit 0 of register A
A ^= (1 << 0);
```

***
