# Looping Part One

> “Eat; Sleep; Love; Repeat” - Instagram Caption.<br><br>
> "Bruh, that's an infinite loop" - Programmer.

**Outline**

- What is this loop thingy ?
- `goto` - Technically not a loop
- `for` loops
- The `break` and `continue` statements

## What is this loop thingy ?

- Loops repeat a block of code until a specified conition is met.
- Ada Lovelace first used a software loop to print out Bernoulli Numbers.
- They are of 3 kinds -
  1. `for` loop
  2. `while` loop
  3. `do while` loop

## `goto` - Technically not a loop

- It is a jump statement that allows us to transfer control of the program to a specified label.
- Avoid using `goto` for it leads to spaghetti code.
- That being said, `goto` statements aren't the problem rather their use in writing bad code is.
- `goto` is useful in jumping out of nested loops.

```C
// Using goto to print Hello World 10 times
    int counter = 1;
again: // label for a goto
    printf("Hello World ");
    if (counter > 10) {
        goto exit_goto;
    }
    ++counter;
    goto again;
exit_goto: // label for another goto
```

- From the above program it is clear how easy it is to get entrapped in a programming hell, with no control over the structure of the program. But surely there is a better way to repeat a block of code.

## `for` loops

<div align="center" style="padding: 2rem;">
	<img src="images/c-for-loop.jpg" style = "max-height: 300px; width: auto;">
    <p style="color: gray">https://www.programiz.com/c-programming/c-for-loop</p>
</div>

- A `for` statement has three parts -

  1. Initialization
  2. Checking Condition
  3. Updation

- We mostly use it when we know the number of times the loop will be executed or the number of iterations.
- It is also called an entry controlled loop, i.e, if the test condition is not satisfied, we won't enter the loop.

Let's take a look at a few code examples -

```C
// Using for loop to print Hello World 10 times
    int counter;
    for (counter = 1; counter <= 10 ; ++counter){
        printf("Hello World ");
    }
```

```C
// Using for loop to print odd numbers in a range
    int num;
    int start = 1;
    int end = 10;
    int counter = start
    for (counter; counter <= end ; ++counter){
        if (counter & 1){
            printf("%d", counter);
        }
    }
```

```C
// Using for loop to find the factorial of a number
    int num;
    int factorial = 1;
    for (int counter = 1; counter <= num ; ++counter){
        factorial = factorial * counter;
    }
    printf("%d", factorial);
```

## The `break` and `continue` statements

- They are both conditional jump statements.
- As soon as `break` is encountered, the control comes out of the loop and the loop is terminated. For example -

```C
// Using the break statement to come out of the for loop
    int num;
    int start = 1;
    int end = 10;
    int counter = start
    for (counter;; ++counter){
        if (counter > end){
            break;
        }
        if (counter & 1){
            printf("%d", counter);
        }
    }
```

- When the `continue` statement is encountered, it skips the current iteration (the rest of the loop body) and moves on to the next iteration. For example -

```C
// Using the break statement to come out of the for loop
    int num;
    int start = 1;
    int end = 10;
    int counter = start
    for (counter;; ++counter){
        if (counter & 1 != 0){
            continue;
        }
        printf("%d", counter);
    }
```
