# Data Types and Variables

> Some nice quote

**Outline**
* Variables and Data Types
* Input and Output functions in `<stdio.h>`
* Data Types in Detail
* Type Specifiers
* Variable naming rules
* Keywords
* The `const` keyword

Let's talk about variables and data. 


## Variables and Data Types

In math, a variable is some value that keeps changing, thus we assign it a name like x or y. The idea of variables in programming is pretty much the same.

In programming terms, you can store values in variables that tend to change. For example, if you built a game, you could store the player's name, score etc. in variables.

Let's look at an example

```C
#include <stdio.h>

int main(){
	int a = 42;
	int b = 13;

	return 0;
}
```

In this example, we declared 2 variables `a` and `b` and stored the values `42` and `13` in them respectively. If you noticed, we had to write `int` before `a` and `b`. 

`int` here is the data type of `a` and `b`, it stands for integer.

In C, when we declare variables, we have to mention the type of data we intend to store in that variable, that's called the **Data Type** of that variable. There are 4 basic data types in C :

* `int` : The Integer type, used to store positive and negative integers
* `float` : The Float type, used to store values with decimal places
* `double` : The Double type, very similar to float, used to store decimal values, the difference is that double has an extended range, it can store twice as many significant digits as compared to a float.
* `char` : The Character type, used to store characters, symbols and special characters. They are formed by enclosing the character in two single quotes (`'A', ';', '?','@'`)

Example

```C
#include <stdio.h>

int main(){
	int age = 10;
	float weight = 72.46;
	double pi = 3.1415926535897;
	char classroom = 'A';
	char question = '?';

	return 0;
}
```


## Input and Output functions in `<stdio.h>`

The `<stdio.h>` header file provides a lot of useful functions. Two of the most used one's are 
* `printf()`
* `scanf()`


### `printf()`

It is used to print data on the screen, we used this function previously to print "Hello, World!", another feature of printf is that we can also use it to print variables

```C
#include <stdio.h>

int main(){
	int a = 42;
	printf("The answer to life, universe and everything is %i\n", a);

	return 0;
}
```

This will give the following output

```shell
$ ./a.out
The answer to life, universe and everything is 42
```

`printf()` replaces the `%i` with the variable passed next to it, `i` here implies that the variable passed is an integer, these are called **format specifiers**. 

We can also use `%d` in place of `%i`, both work for printing integers. A list of all the basic format specifiers is given below

* `%i` or `%d` : for integers
* `%c` : for characters
* `%f` : for floats and doubles
* `%e` : for floats in scientific format, that is 12.67 will be printed as 1.267000e+01

Example

```C
#include <stdio.h>

int main(){
    int age = 50;
    float weight = 72.46;
    double pi = 3.1415926535897;
    char classroom = 'A';
    char question = '?';

	printf("C is almost %d years old\n", age);
	printf("The satellite weighs %f tons\n", weight);
	printf("The satellite weighs %e tons\n", weight);
	printf("My favourite constant is %f\n", pi);
	printf("Where is class %c %c\n", classroom, question);

	// you can also pass multiple variables

	printf("%i %f %f\n", age, weight, pi)

    return 0;
}
```

The output will be

```shell
$ ./a.out
C is almost 50 years old
The satellite weighs 72.459999 tons
The satellite weighs 7.246000e+01 tons
My favourite constant is 3.141593
Where is class A ?
50 72.459999 3.141593
```

### `scanf()`

It is used to take input from the user and store that in a variable using the same format specifiers we used in `printf()`


## Data Types in Detail



## Type Specifiers






## Variable naming rules



## Keywords



## The `const` keyword



