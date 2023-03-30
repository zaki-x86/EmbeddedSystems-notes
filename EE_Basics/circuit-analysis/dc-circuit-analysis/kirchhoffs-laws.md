# Kirchhoff's Laws

Kirchhoff's laws are two laws that describe the behavior of electric circuits. They are named after Gustav Kirchhoff, a German physicist who developed them in the 19th century. The first law (**KVL: Kirchhoff's Voltage Law**) states that the sum of the voltages around a closed loop in a circuit is zero. The second law (**KCL: Kirchoff's Current Law**) states that the sum of the currents entering a node is equal to the sum of the currents leaving that node.

#### KCL

KCL states that the sum of the currents entering a node is equal to the sum of the currents leaving that node. This means that the current entering a node is equal to the current leaving that node. This is illustrated in the figure below:

![kcl](https://dwma4bz18k1bd.cloudfront.net/tutorials/Kirchhoff%E2%80%99s-Current-Law.jpg)

**Source:** [Circuit Bread](https://www.circuitbread.com/tutorials/how-to-solve-complicated-circuits-with-kirchhoffs-current-law-kcl)

**Sample Problem**

Analyze in the circuit below:

![sample problem](https://dwma4bz18k1bd.cloudfront.net/tutorials/Kirchhoff%E2%80%99s-Current-Law-Tutorial-Problem-1-Circuit-A.jpg)

Given: $I\_1 = 1A$ $I\_2 = 2A$ $R\_1 = 10$ $R\_2 = 20$ $R\_3 = 30$ **Source**: [Circuit Bread](https://www.circuitbread.com/tutorials/how-to-solve-complicated-circuits-with-kirchhoffs-current-law-kcl)

> When we ask to **analyze** a circuit, we are basically trying to know everything about this circuit, basically, find every value that is unknown.

**Analysis:**

1. Review what has been given and what you need. In this problem, we have 3 resistors and their value, 2 currrent sources and their values. We need to find the current in the third resistor, $I\_3$. On first look, it doesn't look like we can solve this problem using the practices of solving resistor circuits, so we need to use KCL or (later KVL).
2. Choose a reference ground, if it hasn't already been defined. Standard practice is to choose buttom node as ground. Therefore, node $ N\_2 $ is the reference ground.
3. Since we don't know the current flowing throught $ R\_3 $, we will use the potential difference across $ R\_3 $ to derive an equation for $ I\_3 $, which leads to the the following equation:

$$I_3 = \frac{V_1 - V_2}{R_3}$$

Since we chose $ N\_2 $ as the reference ground, then $ V\_2 = 0 $:

$$I_3 = \frac{V_1}{R_3}$$

$$I_3 = \frac{V_1}{30} \space \space eq(1)$$

4. Now, we will use KCL to derive another equation for $ I\_3 $ because we have 2 unknowns, so we need 2 equations:

$$I_3 = I_1 + I_2$$

$$I_3 = 3 \space \space eq(2)$$

> **Note:** We assumed the direction of unknown current to be towards $ N\_2 $ till we are proven if we're right or wrong after we do the math.

5. Now, we will substitute $ I\_3 $ from equation (1) into equation (2):

$$\frac{V_1}{30} = 3$$ $$V_1 = 90$$

**More complicated problem**

**Summary: Steps to solve any problem using KCL**

1. Review what has been given and what you need.
2. Choose a reference ground, if it hasn't already been defined.
3. Use the potential difference across the unknown resistor(s) to derive an equation for the unknown current.
4. Use KCL to derive another equation for the unknown current.
5. Solve the derived equations to find the unknown values.

#### KVL
