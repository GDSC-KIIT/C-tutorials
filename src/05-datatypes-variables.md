# Data Types and Variables

> “Don’t worry if it doesn’t work right.  If everything did, you’d be out of a job.” <br> - (Mosher’s Law of Software Engineering)

**Outline**
* Variables and Data Types
* Input and Output functions in `<stdio.h>`
* Type Specifiers and Data Type Sizes
* Variable naming rules and Keywords
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
* `char` : The Character type, used to store characters, symbols and special characters. They are formed by enclosing the character in two single quotes (`'A', ';', '?', '@'`)
* `void` : it means "nothing", you cannot declare `void` variables, it is mostly used for functions that return nothing, we will have a look at functions in Ch 11

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
* `%f` and `%lf` : for floats and doubles respectively
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

It is used to take input from the user and store that in a variable using the same format specifiers we used in `printf()`. Lets look at an example

```C
#include <stdio.h>

int main(){
	int a;

    printf("Enter an int: ");
	scanf("%d", &a);
	printf("a = %i\n", a);

	// multiple input in a single line
	float b;
	char c;

	printf("Enter a float and a character (seperated by a space): ");
	scanf("%f %c", &b, &c);
	printf("b = %f\n", b);
	printf("c = %c\n", c);

	return 0;
}
```

Output,

```shell
$ ./a.out
Enter an int: 46
a = 46
Enter a float and a character (seperated by a space): 3.4 k
b = 3.400000
c = k
```

We can also do inputs on multiple lines,

```C
#include <stdio.h>

int main(){
	int a;
	float b;
	char c;

    printf("Enter an int: ");
	scanf("%d", &a);
	
	printf("Enter a float: ");
	scanf(" %f", &b);
	
	printf("Enter a character: ");
	scanf(" %c", &c);

	printf("a = %i\n", a);
	printf("b = %f\n", b);
	printf("c = %c\n", c);

	return 0;
}
```

Output,

```shell
$ ./a.out
Enter an int: 12
Enter a float: 1.2
Enter a character: d
a = 12
b = 1.200000
c = d
```

If you notice, there is a space before `%f` and `%c`. Those are there for a reason, if we remove them, the program behaves very weirdly. All the inputs are not taken properly. That happens because when we press enter for the first input, that `\n` character gets fed into the next `scanf` and we directly jump to the next input after that. To prevent this, we put a space in before.


## Type Specifiers and Data Type Sizes

When we declare variables, what happens in the background is that memory gets allocated in the RAM so that we can store values in that allocated memory. Thats how variables work.

Along with data types, there are other keywords called **type specifiers**, these keywords let us tell the compiler some more details about the data types, the type specifiers in C are

* `short` : to allocate half the size of the data type
* `long` : to extend the size of the data type
* `long long` : to extend the size of the data type even more
* `signed` : variable can store positive and negative values
* `unsigned` : variable will store only positive values

All variables are signed by default.


Each data type has its own size in terms of bytes that are allocated. The table below specifies the number of bytes

| Data Type | Size in Bytes | Range                                 |
|-----------|---------------|---------------------------------------|
| `char`    | 1             | $$-2^{7} \space to \space 2^{7}-1$$   |
| `int`     | 4             | $$-2^{31} \space to \space 2^{31}-1$$ |
| `float`   | 4             | $$-2^{31} \space to \space 2^{31}-1$$ |
| `double`  | 8             | $$-2^{63} \space to \space 2^{63}-1$$ |

Along with type Specifiers

### Characters

| Data Type       | Size in Bytes | Range                               |
|-----------------|---------------|-------------------------------------|
| `char`          | 1             | $$-2^{7} \space to \space 2^{7}-1$$ |
| `unsigned char` | 1             | $$0 \space to \space 2^{8}-1$$      |


### Integers

| Data Type               | Size in Bytes | Range                                 |
|-------------------------|---------------|---------------------------------------|
| `int`                   | 4             | $$-2^{31} \space to \space 2^{31}-1$$ |
| `unsigned int`          | 4             | $$0 \space to \space 2^{32}-1$$       |
| `short int`             | 2             | $$-2^{15} \space to \space 2^{15}-1$$ |
| `unsigned short int`    | 2             | $$0 \space to \space 2^{16}-1$$       |
| `long int`              | 8             | $$-2^{63} \space to \space 2^{63}-1$$ |
| `unsigned long int`     | 8             | $$0 \space to \space 2^{64}-1$$       |


### Floating-Point Types

| Data Type     | Size in Bytes  | Range                                 |
|---------------|----------------|---------------------------------------|
| `float`       | 4              | $$-2^{31} \space to \space 2^{31}-1$$ |
| `double`      | 8              | $$-2^{63} \space to \space 2^{63}-1$$ |
| `long double` | 10             | $$-2^{79} \space to \space 2^{79}-1$$ |

C does not support an `unsigned float` or `unsigned double`

The `scanf()` format specifiers for `long` and `short` are `l` and `h` respectively. So for `long int`, it is put as `%li` and short int can be put as `%hi`.


## Variable naming rules and Keywords

When we pick names for variables, there are a few simple rules we have to follow :

1. Variable names cannot be C keywords.
2. Variable names have to start with either a letter or an underscore.
3. Variable names can only contain letters, digits and underscores.
4. Variable names cannot have spaces.
5. Variable names cannot start with numbers.

**Valid variable names :**

`sum`
`pieceFlag`
`i`
`J5x7`
`Number_of_moves`
`_sysflag`


**Invalid variable names :**

* `sum$value` : `$` is not a valid character.
* `piece flag` : Embedded spaces are not permitted.
* `3Spencer` : Variable names cannot start with a number.
* `int` : int is a reserved word.

### Keywords

Keywords are specific words that have a special meaning to the C compiler, for example the keyword `int`, it has a specific meaning, it tells the compiler to create an integer. We cannot use keywords as variable names, for example `int int = 0` is invalid.

C has a total of 32 keywords. 

|||||
|---------|----------|----------|--------|
|auto     |	break    | case     | char   |
|const    |	continue | default  | do     |
|double   |	else     | enum     | extern |
|float    |	for      | goto     | if     |
|int      |	long     | register | return |
|short    |	signed   | sizeof   | static |
|struct   |	switch   | typedef  | union  |
|unsigned |	void     | volatile | while  |



## The `const` keyword

If we add the `const` keyword before any variable, we cannot change it to another value later. For example,

```C
#include <stdio.h>

int main(){
	const float pi = 3.1415;
	pi = 23;
	return 0;
}
```

if we run this, 

```shell
$ ./a.out
data-types.c: In function ‘main’:
data-types.c:5:5: error: assignment of read-only variable ‘pi’
    5 |  pi = 23;
      |
```
