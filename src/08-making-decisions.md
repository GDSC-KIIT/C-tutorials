# Making Decisions using if else

<div align="center" style="padding: 2rem;">
	<img src="images/conditionals.png" style = "max-height: 300px; width: auto;">
    <p style="color: gray">If Shakespeare were a programmer</p>
</div>

**Outline**

- The Decision Making Process
- Using Relational and Logical Operators
- Using the Ternary Operator
- The `if` statement
- Better Decisions with `else` and `else if`
- Nested Conditions
- The `switch` statement

## The Decision Making Process

We, as humans, make a lot of decisions in our day to day life. Even you, the reader, made a decision to go through this book. This decision was made (or evaluated True) based on certain condtions like -

1. I need a quick recap of C.
2. The quality of the content looks good.
3. The author can read my mind :p

Imagine if a computer can do this. A robot in the year 2050 deciding to enslave the human race or not based on a set of conditions. How revolutionary would that be? :")

But we are far from it as computers cannot decide these conditions or parameters on their own. They need human intervention to get a list of all neccessary conditions and then they can make a decision based on whether those conditions are satisfied or not. The computer achieves this with the help of conditional statements.

Consider this simple problem for the rest of the lesson - Your dad has to decide on how to react based on the grade you get in your exam. We'll start with coming up the basic conditions and then we'll build on top of that.

## But how are conditions evaluated ?

Remember relational and logical operators from the [Operators](https://dsc-kiit.github.io/C-tutorials/06-operators.html) lesson? Well, they provide a huge range of comparisions we can do on the input enetered by the user to decide whether our condition is evaluated as True or False. For example -

1. If grade is not equal to 'F', dad will praise you. In code it can be written as - **grade != 'F'** (**!=** is a **relational** operator)
2. If your grade is equal to 'E' or 'F', dad will scold you. In code it can be written as - **grade == 'E' || grade == 'F'** (**==** is a **relational** operator and **||** is a **logical** operator)

## Using the Ternary Operator

We've already learnt how to make a decision using ternary or conditional operators. For example -

```C
// To find the maximum of two numbers
int c = (a > b)? a : b;
```

Here, **a > b** is a condition. And depending upon the input, the program can make a decision on whether **a** is greater than **b** or not.

## The `if` statement

## Better Decisions with `else` and `else if`

## Nested Conditions

## The `switch` statement
