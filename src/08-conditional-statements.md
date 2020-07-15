# Making Desicions using if else 

<div align="center" style="padding: 2rem;">
	<img src="images/conditionals.png" style = "max-height: 300px; width: auto;">
    <p style="color: gray">If Shakespeare were a programmer</p>
</div>

**Outline**

- The Decision Making Process
- Using Relational and Logical Operators
- Using the Ternary Operator
- The `if` statement
- The `else` statement
- The `else if` statement
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

1. If grade is not equal to 'F', dad will praise you. In code it can be written as - `grade != 'F'` (`!=` is a **relational** operator)
2. If your grade is equal to 'E' or 'F', dad will scold you. In code it can be written as - `grade == 'E' || grade == 'F'` (`==` is a **relational** operator and `||` is a **logical** operator)

## Using the Ternary Operator

We've already learnt how to make a decision using ternary or conditional operators. Continuing with the example above -

```C
printf((grade != 'F')? "Praise" : "Scold");
```

Here, `grade != 'F'` is a condition. And depending upon the input (grade), the program can make a decision on whether `Praise` or `Scold` should be printed.

## The `if` statement

The basic structure of an `if` block is -

```
if condtion is true then
    do some task
```

Therefore the syntax becomes -

```C
if (condition) {
    // do some task
}
```

The `if` statement evaluates the condition inside the `()` or parenthesis and if it is true then the statements inside the `if` block (within curly braces) is executed. Continuing with the question above, the code will look like this -

```C
if (grade != 'F') {
    printf("Praise");
}
if (grade == 'F') {
    printf("Scold");
}
```

But our program has to check if grade is equal to 'F' two times but it's common sense that if the first condition fails, then our grade should be equal to 'F'. There is a better way of writing this using `else`.

## The `else` statement

The basic structure of an `if else` block is -

```
if condtion is true then
    do some task
else
    do another task
```

Therefore the syntax becomes -

```C
if (condition) {
    // do some task
}
else {
    // do another task
}
```

If the condition inside the `if` statement is True, then the `if` block is executed and the whatever's inside the `else` block is skipped and if the condition is evaluted as False, the opposite happens. Let's write a better program for the above problem.

```C
if (grade != 'F') {
    printf("Praise");
}
else {
    printf("Scold");
}
```

This also looks pretty similar to the conditional / ternary operator.

## The `else if` statement

In real life, our conditions are not as binary as an `if` - `else` statement. There can be multiple outputs for multiple conditions. To handle that, we have `else if`.

The basic structure of an `if - else if - else` block is -

```
if condtion is true then
    do task 1
else if another condition is true
    do task 2
else
    do task 3
```

Therefore the syntax becomes -

```C
if (condition) {
    // do task 1
}
else if (another condition) {
    // do task 2
}
else {
    // do task 3
}
```

Starting from the first `if` statement, we keep on checking if a condition is satisfied or not. If any one of the conditions is evaluated as True, its body is executed and then the control comes out of the entire `if - else if - else` block. So even if more than one condition is True in the `if - else if - else` block, it won't matter because after the evaluation of the body of the first True condition, the control will skip all other conditions and come out of the `if - else if - else` block.
Note that we can have endless `else if`s in between.
Now, let's introduce a couple other conditions in the above program-

- If grade is equal to 'A' -> Gift
- If grade is equal to 'F' -> Scold
- Any thing other than that -> Praise

This will translate into -

```C
if (grade == 'A') {
    printf("Gift");
}
else if (grade == 'F') {
    printf("Scold");
}
else {
    printf("Praise");
}
```

## Nested Conditions

We can also have another `if` or `if else` or `if else if` statement inside an `if` statement like this -

```C
if (grade != 'F') {
    if (grade == 'A') {
        printf("Gift");
    }
    else {
        printf("Praise");
    }
}
else {
    printf("Scold");
}
```

## The `switch` statement

As the number of conditions grow, the `if - else if - else` block grows and becomes harder to read. Here is where the `switch` statement comes in and allows us to choose one code block (output) among any options (outputs) based on an expression. Once this expression is evaluated, it is checked against various `case`s (each containing their own own code) within the switch block and once a match is found, the code block corresponding to that matched case is executed.

Therefore the syntax becomes -

```C
switch (expression) {
    case constant1:
    // some output
    break;

    case constant2:
    // some output
    break;

    default :
    // default output
}
```

Here there is a `break` statement after every block because after some code block is executed, the control needs to come out of the `switch` block. `break` does exactly this. We will discuss more about in the Loops chapter.

`default` case is executed when none of the cases match the expression value. We don't require a `break` after this because the `default` case is the last to be executed and the control will automatically come out of the `switch` block after that. Note that `default` is optional but helps catch all possible cases.

Continuing with out above question, let's convert the `if - else if - else` block to a `switch case` one.

```C
switch (grade) {
    case 'A':
        printf("Gift");
        break;
    case 'F':
        printf("Scold");
        break;
    default :
        printf("Praise");
}
```

The code seems more readable and easily extendable now.

**Bonus** - If we don't put a `break` statement, then **fall-through** occurs, where all cases below the matched case are also executed since the control isn't able to come out of the `switch` block automatically. An interesting use case of fall-through is to check whether an alphabet is a vowel or not.

```C
switch (letter) {
    case 'A':
    case 'E':
    case 'I':
    case 'O':
    case 'U':
        printf("Vowel");
        break;
    default:
        printf("Not Vowel");
}
```
