# Coding and Number Systems

### Introduction

Binary numbers are numbers expressed in the base-2 numeral system or binary numeral system, which uses only two symbols: typically "0" (zero) and "1" (one). The base-2 numeral system is a positional notation with a radix of 2. Because of its straightforward implementation in digital electronic circuitry using logic gates, the binary system is used internally by almost all modern computers and computer-based devices. Each digit is referred to as a **bit**.

Data in digital circuits and computers is stored and transmitted as a series of zeros and ones and so various numbering systems are used to represent the data. Conveniently, binary numbers have only two digits that are 0 and 1, so every piece of data (number) can be represented using a binary numbering system.

### Overview of Coding and Number Systems

#### Binary Coding

In computers, binary is used as the basic language for representing data and instructions. For instance, a byte of data (8 bits) can represent numbers from 0 to 255 in binary, as each bit can be either 0 or 1. Binary is also used in operations such as bitwise logical operations, shifting, and masking.

Why binary? Simply because logic circuits are primitive constructs cheaply built in huge quantities. By restricting the electronics to two values only—on and off—we care little if the voltage drifts from 2 to 5.

**Converting decimals to binary**

**Positive Integers (decimal to binary)**

To convert a decimal number to binary, you can use the following steps:

1. Start by dividing the decimal number by 2 and writing down the remainder.
2. Divide the result of the previous division by 2 again, and write down the remainder.
3. Continue dividing the result by 2 and writing down the remainders until the result is 0.
4. Write down the remainders in reverse order to get the binary representation.

**For example, to convert the decimal number 13 to binary, you can use the following steps:**

1. Divide 13 by 2 and write down the remainder: 13/2 = 6 with remainder 1.
2. Divide 6 by 2 and write down the remainder: 6/2 = 3 with remainder 0.
3. Divide 3 by 2 and write down the remainder: 3/2 = 1 with remainder 1.
4. Divide 1 by 2 and write down the remainder: 1/2 = 0 with remainder 1.
5. Write down the remainders in reverse order to get the binary representation: 1101.

**Positive Real Numbers (decimal to binary)**

**To convert the decimal number 0.625 to binary, you can use the following steps:**

1. Multiply 0.625 by 2 and write down the integer part: 0.625 × 2 = 1.25, integer part = 1.
2. Multiply 0.25 by 2 and write down the integer part: 0.25 × 2 = 0.5, integer part = 0.
3. Multiply 0.5 by 2 and write down the integer part: 0.5 × 2 = 1, integer part = 1.
4. Write down the integer parts to get the binary representation: 0.101.
5. If the binary representation is not exact, add a 1 to the right of the binary representation to indicate that the number is not exact.

**To convert the decimal number 13.375 to binary, you can use the following steps:**

1. Convert the integer part of the decimal number to binary: 13 = 1101.
2. Convert the fractional part of the decimal number to binary: 0.375 = 0.011.

**Converting binary to decimal**

**Positive Integers (binary to decimal)**

**To convert a binary number to decimal, you can use the following steps:**

1. Start by multiplying the rightmost digit by $2^0$.
2. Multiply the next digit by $2^1$, then $2^2$, then $2^3$, and so on.
3. Add the results of the multiplications to get the decimal representation.

You can use the follow formula to convert a binary number to decimal:

$$\sum_{i=0}^{n} b_i \times 2^i$$

where $b\_i$ is the $i^{th}$ digit of the binary number, and $n$ is the number of digits in the binary number.

**For example, to convert the binary number 1101 to decimal, you can use the following steps:**

1. Multiply the rightmost digit by $2^0$: 1 × $2^0$ = 1.
2. Multiply the next digit by $2^1$: 1 × $2^1$ = 2.
3. Multiply the next digit by $2^2$: 0 × $2^2$ = 0.
4. Multiply the next digit by $2^3$: 1 × $2^3$ = 8.
5. Add the results of the multiplications to get the decimal representation: $1 + 2 + 0 + 8 = 11$.

**Positive Real Numbers (binary to decimal)**

**To convert a binary real number to decimal, you can use the following steps:**

1. Convert the integer part of the binary number to decimal.
2. Convert the fractional part of the binary number to decimal by multiplying each digit by $2^{-n}$, where $n$ is the position of the digit.
3. Add the results of the two conversions to get the decimal representation.

**To convert the binary number 0.101 to decimal, you can use the following steps:**

1. Multiply the rightmost digit by $2^0$: 1 × $2^0$ = 1.
2. Multiply the next digit by 2^1: 0 × $2^1$ = 0.
3. Multiply the next digit by 2^2: 1 × $2^1$ = 4.
4. Add the results of the multiplications to get the decimal representation: $1 + 0 + 4 = 5$.

**To convert the binary number 1101.011 to decimal, you can use the following steps:**

1. Convert the integer part of the binary number to decimal: 1101 = 13.
2. Convert the fractional part of the binary number to decimal: 0.011 = 0.375.

**Working with Negative Numbers**

Negative numbers are an essential part of mathematics and computer science, and understanding how they are stored and manipulated is crucial to understanding how computers work.

The binary system used by computers presents a challenge when it comes to representing negative numbers. In the decimal system used by humans, negative numbers are represented with a minus sign (-) in front of the number. But in binary, there is no way to indicate a negative value using a simple sign or symbol.

To get around this problem, computer scientists came up with a method known as **two's complement**. In this system, negative numbers are represented by the two's complement of their positive counterparts. The two's complement of a number is obtained by taking the complement (inverting all the bits) of the number and adding 1 to the result.

For example, the two's complement of 13 is 1111 0011. To get this number, we first invert all the bits of 13 to get 1111 1100. Then we add 1 to the result to get 1111 1101. Finally, we add 1 to the result to get 1111 1110. Then we add 1 to the result to get 1111 1111. This is the two's complement of 13.

Using this method, computers are able to represent both positive and negative numbers using the same number of bits. For example, a 16-bit integer can represent values from -32,768 to 32,767 using two's complement. This is because the most significant bit (**MSB** : the leftmost bit) is used as a sign bit, with 0 indicating a positive value and 1 indicating a negative value.

When performing arithmetic operations with negative numbers, the two's complement system ensures that the same circuitry can be used for both positive and negative values. For example, to add two numbers in two's complement form, the circuitry simply performs a binary addition, with any overflow bits discarded. The resulting value will automatically be in two's complement form, whether it is positive or negative.

**How do computers understand floating point numbers**

Now that we understand how decimals are represented in binary, we can move on to floating point numbers. Floating point numbers are a way of representing real numbers in binary. The binary representation of a floating point number is made up of three parts:

1. The **sign bit**, which is 1 if the number is negative and 0 if the number is positive.
2. The **exponent**, represents the magnitude of the number, which is a binary number that represents the power of 2 that the mantissa is multiplied by.
3. The **mantissa**, which is a binary number that represents the significant digits of the number (the number itself).

The exponent is usually represented in biased notation, which means that a fixed value is added to the true exponent to ensure that it is always positive. This bias value is typically $2^{(k-1)}-1$, where $k$ is the number of bits used to represent the exponent. For example, in a 32-bit floating-point format, the bias value is 127.

The mantissa, meanwhile, represents the fractional part of the number. This is where floating-point numbers differ from integers, as they can represent values with a fractional component. The mantissa is usually **normalized**, which means that the first bit is assumed to be 1 and is not actually stored. This allows for more precision and flexibility when representing real numbers.

**For example, the floating-point number -6.75 is represented as follows:**

1. Convert the integer part of the number to binary: 6 = 110 (ignore the negative sign for now).
2. Convert the fractional part of the number to binary: 0.75 = 0.11.
3. Combine the integer and fractional parts of the number: 110.11.
4. Normalize the mantissa: 1.1011. To normalize the mantissa, we simply move the decimal point to the right until the first digit is 1. In this case, the decimal point is moved two places to the right, so the mantissa is 1.1011.
5. Calculate the exponent bias and calculate the exponent A bias of ($2^{8-1} - 1 = 127$) is added to the exponent to ensure that it is always positive. In this case, the exponent is 2, so the biased exponent is 129. the exponent field is an 8-bit field that can represent values from 0 to 255. The biased exponent is 129, which is represented in binary as 1000 0001.
6. Determine the significand (mantissa) and convert it to binary The significand is the mantissa multiplied by 2 to the power of the exponent. In this case, the significand is 1011. We will use the remaining 23 bits in the floating point number to represent the significand, so we will need to pad the significand with zeros until we have 23 bits. The padded significand is 1011 0000 0000 0000 0000 000.
7. Combine the sign bit, biased exponent, and significand to get the binary representation of the floating point number 1 1000 0001 1011 0000 0000 0000 0000 0000

#### Hexadecimal Numbers

**What is Hexadecimal**

Hexadecimal numbers are a way of representing numbers using the 16 digits 0-9 and the letters A-F. Hexadecimal numbers are often used in computer science because they are easier to work with than binary numbers. For example, the hexadecimal number 0x1A is easier to read than the binary number 0001 1010.

Hexadecimal numbers are also used to represent colors in HTML and CSS. For example, the color red is represented as #FF0000, which is the hexadecimal representation of the binary number 1111 1111 0000 0000 0000 0000.

Hexadecimals use letters to represent the numbers 10-15. The letters A-F are used to represent the numbers 10-15, with A representing 10, B representing 11, C representing 12, D representing 13, E representing 14, and F representing 15.

**Converting from Decimal to Hexadecimal**

To convert a decimal number to hexadecimal, you can use the following steps:

1. Divide the decimal number by 16.
2. Write down the remainder.
3. Divide the quotient by 16.
4. Write down the remainder.
5. Repeat steps 3 and 4 until the quotient is 0.
6. Reverse the order of the remainders to get the hexadecimal representation of the number.

**For example, to convert the decimal number 42 to hexadecimal, you can use the following steps:**

1. Divide 42 by 16: 42 ÷ 16 = 2 with remainder 10.
2. Divide 2 by 16: 2 ÷ 16 = 0 with remainder 2.
3. Reverse the order of the remainders: 2A.

#### Operations on Binary Numbers

**Addition**

**Subtraction**

### Summary

In this lesson, we learned about the binary number system and how it is used to represent numbers in computers. We also learned about the hexadecimal number system and how it is used to represent numbers in computers. We also learned about the binary number system and how it is used to represent numbers in computers. We also learned about the hexadecimal number system and how it is used to represent numbers in computers.

***

**Next**: Combinatorial Logic
