# Operators

> “Computers are better than we are at arithmetic, not because computers are so good at it, but because we are so bad at it.” - Isaac Asimov.<br><br>
> "Oof" - Quote Reader.

**Outline**

- Operators vs Operands
- Unary Operators
- Binary Operators
- Ternary Operators
- Heirarchy Table.

## Operators vs Operands

Let's get the formal defination out of the way.

- Operator performs some mathematical or logical operation on the operand.
- Operand is the variable/ constant on which the operator is operating.

Example, please?

<div align="center" style="padding: 2rem;">
	<img src="images/operators-operands.png">
</div>

Here, in the expression, **a + b**, **+** is denoted as an operator in programming because it performs a mathematical operation (addition) on the elements **a** and **b** which are therefore called operands. Depending upon the number of operands, we have - Unary, Binary and Ternary operators.

## Unary Operators

- Always acts on a single operand.
- **++** (unary increment operator) increases the value by 1 and **--** (unary decrement operator) decreases the value by 1.
- They are called prefix or postfix depending on whether they are placed before or after the operand.

<div align="center" style="padding: 2rem;">
	<img src="images/prefix-postfix.png">
</div>

### Difference between prefix and postfix

The keyword to remember in prefix operations is **change before use** and in postfix operations is **change after use**. For example -

```C
int a = 3;
int b = ++a;  /* The value stored in b will be 4, because first the value of a is
				 incremented from 3 to 4 (change before use) and then it is assigned
				(used) to b */
int c = a++;  /* The value stored in c will be 4 (current value of a is 4 as it was
				incremented when assigned to b), because first the value of a is
				assigned (used) to c and then it is incremented from 4 to 5 (change
				after use).*/
int d = a;    // Since the current value of a is 5, the value stored in d will be 5.
```

For a more visual example, refer [here](https://www.youtube.com/watch?v=FALus1PqmM8), timestamp 2:42 - 7:00.

## Binary Operators

Always act on two operands. Its different types are -

### Arithmetic Operators

- These operators perform a mathematical operation on the operands.
- They are : + - \* / %

```C
int add = 5 + 2; // 7 due to addition
int sub = 5 - 2; // 3 due to substraction
int mul = 5 * 2; // 10 due to multiplication
int div = 5 / 2; // 2 not 2.5, since division between two integers produces an integer
float div_float = 5.0 / 2.0 // 2.5 since the operands are floating points
int rem = 5 % 2; /* 1 since it is the remainder when 5 is divided by 2. The modulo operator
					only works on integer operands beacause of the following equation being
					generated when you divide one number with another :
					dividend = quotient*divisor + remainder
					Here all of these are integer values. To find the modulo of floating
					point numbers you need to use fmod() provided in the math library*/
```

### Relational Operators

- These operators find a relationship between the **operands**.
- The relationships can be : > < >= <= == !=
- Returns (the output) either 1 or 0 based on whether the relationship is satisfied (is true) or not (is false).

```C
/* We can operate on characters just like we operate on integers as behind the scenes
   a character variable holds its unique ASCII value (which is an integer value), not
   the character itself */
char a = 'a'; // ASCII value 97
char b = 'b'; // ASCII value 98
printf("%d", a > b);  // 0 as 97 is not greater than 98
printf("%d", a < b);  // 1 as 97 is less than 98
printf("%d", a <= b); // 1 as 97 less than if not equal to 98
printf("%d", a >= b); // 0 as 97 is neither greater than not equal to 98
printf("%d", a == b); // 0 as 97 is not equal to 98
printf("%d", a != b); // 1 as 97 is not equal to 98

```

The complete ASCII table can be found [here](https://www.techonthenet.com/ascii/chart.php).

### Logical Operators

- These operators find a relationship between **expressions**, which in turn may be made of relational operators, for example **a > b** is an expression.

- They are -

  1. && (logical AND, evaluated true only and only if all the individual expressions evaluate as true)
  2. || (logical OR, evaluated true if any one of the expressions is true)
  3. ! (NOT operator, complements the result of an expression, true evaluates to false and vice-versa).

- Returns (the output) either 1 or 0 based on whether the relationship is satisfied (is true) or not (is false).

```C
char a = 'a'; // ASCII value 97
char b = 'b'; // ASCII value 98
printf("%d", (a < b) && (a > b)); /* 0 because even though the first expression is true, the second expression
									is not, therefore logical AND evaluates the entire expression as false */

printf("%d", (a < b) || (a > b)); /* 1 because even though the second expression is false, the first expression
									is true, and since we need only one expression to be true, logical OR
									evaluates the entire expression as true. Also note that once logical OR
									finds a true expression it doesn't check the rest of the expressions becuase
									no matter what the value of the later will be, the entire expression will
									result in true. This is known as short circuit evaluation. */

printf("%d", !(a < b)); 	  /* 0 because a is less than b and hence the value of that expression is 1 but
									because of the not operator, true changes to false and hence 0 is printed */
```

### Bitwise Operators

- Data is stored in a computer in the form of bits.
- Bitwise operators, treat their operands as a string of bits (1s and 0s).
- They are faster when compared to arithmetic operators like integer modulo and division.
- The operators are - & (bitwise AND), | (bitwise OR), ^ (bitwise XOR), << (bitwise left shift), >> (bitwise right shift).

```C
// code to check if a number is odd or not
bool is_odd = (number & 1) ? true : false;
```

## Ternay Operators

- Always act on three operands.
- It is represented by **? :**
- Example - a ? b : c. If expression **a** is true then return (output) **b**, and if it is false, then return **c**.

```C
// Code for maximum of 2 numbers
int a = 1;
int b = 2;
int c = (a > b)? a : b; /* 2  because a>b is evaluated as false therefore the second part, b,
						   is executed instead of a */
```

To see the code and explanation for finding the maximum between three numbers, refer [here](https://www.youtube.com/watch?v=FALus1PqmM8), timestamp 21:43 - 23:03.

## Operator Precedence

In an expression, containing various operators, not all operators are evaluated at once. Just like the BODMAS rule in Maths, we have a precedence table in C too, found [here](http://web.cse.ohio-state.edu/~babic.1/COperatorPrecedenceTable.pdf).

```C
int a = 2 > !3 && 4 - 1 != 5 || 6; // 1 according to the operator precedence table
```

For an a more visual and detailed explanation for the above example, refer [here](https://www.youtube.com/watch?v=FALus1PqmM8), timestamp 25:08 - 28:46.
