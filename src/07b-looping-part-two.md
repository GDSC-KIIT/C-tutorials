# Looping Part Two

<div align="center" style="padding: 2rem;">
	<img src="images/infinite-loop.png" style = "max-height: 300px; width: auto;">
    <p style="color: gray">https://xkcd.com/1411/</p>
</div>

**Outline**

- `while` loops
- Infinite loops in `for` and `while`
- `do while` loops
- Nested Loops
- Nested Loop Tricks

## `while` loops

Remember how `for` loops had 3 parts - initialization, condition and updation that had to be defined while defining the loop. We also saw how we could skip all of these parts and still the loop would work. But that kind of defeats the purpose of the `for` loop which is to iterate over a certain loop body a fixed number of times. But what if we don't know before hand how many times the loop body should be executed. Here's where the dynamic `while` loop comes into play.

<div align="center" style="padding: 2rem;">
	<img src="images/c-while-loop.jpg" style = "max-height: 300px; width: auto;">
    <p style="color: gray">https://www.programiz.com/c-programming/c-do-while-loops</p>
</div>

The syntax is -

```C
while (condition) {
    // loop body
}
```

Till this condition is satisfied, the loop body will be executed, which means, the `while` loop is an entry controlled loop.

Let's take a look at a few code examples -

```C
// Print numbers 1 to 5
int counter = 1;          // initialization
while (counter <= 5) {    // condition
    printf("%d", counter);
    ++counter;            // updation
}
```

```C
// Print all the Fibonacci numbers less than limit
int limit;
int first_term = 0, second_term = 1;
int next_term = first_term + second_term;
while (first_term <= limit) {
    printf("%d ", first_term);
    first_term = second_term;
    second_term = next_term;
    next_term = first_term + second_term;
}
```

## Infinite loops in `for` and `while`

```C
for (;;) {
}
```

```C
while (1) {
}
```

## `do while` loops

<div align="center" style="padding: 2rem;">
	<img src="images/c-do-while-loop.jpg" style = "max-height: 300px; width: auto;">
    <p style="color: gray">https://www.programiz.com/c-programming/c-do-while-loops</p>
</div>

The syntax is -

```C
do {
   // loop body
} while (condition);
```

The `do while` loop is similar to the `while` loop except that is an exit-controlled loop which means that the condition is checked after the loop body. This is an important property because even if the condition is not satisfied, the loop will be executed atleast once. For example -

```C
// The output will be 1
int counter = 0;
do {
    printf("%d", counter);
} while (counter > 0);
```

Even though the condition `counter > 0` was not satisfied, the loop body got executed atleast once. So what possibly could be the use case for this? An interesting use case is while taking input -

```C
float pos_num;
do {
    printf("Enter a positive number : ");
    scanf("%f", &pos_num);
} while (pos_num >= 0);
```

## Nested Loops

- It is a loop within a loop.
- The first iteration of the outer loop triggers the inner loop which, in turn, is executed to completion. In the second iteration of the outer loop, the inner loop is triggered again and so on.
- Useful for printing patterns or representing output in two dimensions.

```C
for (row = 1; row <= num; row++) {
    for (column = 1; column <= num; column++) {
        printf("%d", column);
    }
    printf("\n");
}
```

## Nested Loop Tricks

- Left aligned triangle -

```C
int num_rows = 3;
for (row = 1; row <= num_rows; row++) {
    for (column = 1; column <= row; column++) {
        printf("%d", column);
    }
    printf("\n");
}
/*
1
12
123
*/
```

- Inverted left aligned triangle -

```C
int num_rows = 3;
for (row = num_rows; row > 0; row--) {
    for (column = row; column > 0; column--) {
        printf("%d", column);
    }
    printf("\n");
}
/*
321
21
1
*/
```

- Right aligned triangle -

```C
int num_rows = 3;
for (row = 1; row <= num_rows; row++) {
    if (num_rows - row) {
        printf("%*c", num_rows - row, ' ');
    }
    for (column = 1; column <= row; column++) {
        printf("%d", column);
    }
    printf("\n");
}
/*
  1
 12
123
*/
```

- Other patterns like right aligned inverted triangle, pyramid, etc, can be made with a combination of the above code.
