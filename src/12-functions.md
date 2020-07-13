# Functions

**Outline**
* What are Functions ?
* Defining Functions
* Arguments and Return Types
* Local and Global Variables
* Scope and Lifetime of Variables
* `static` Variables
* `static` Functions
* Arrays and Functions
* Recursive Functions


## What are Functions ?

Functions are the building blocks of large programs in C. 

When you hear functions, you probably think of functions as we learn them in math, functions in C work in a similar way. There are multiple ways to think of functions and each one of them offers a unique perspective into the role of functions. 

Let's look at an example then we will formally define a function

```C
#include <stdio.h>

void greet() {
	printf("Hello Everyone\n");
	printf("Greetings and Welcome\n");
	printf("We hope you enjoy this\n");
}

int square(int x){
	int answer = x*x;
	return answer;
}

int main(){
	greet();

	int a = square(5);
	printf("Square of 5 is %d\n", a);
	
	return 0;
}
```

`square` and `greet` are functions, the output will be :

```shell
$ ./a.out
Hello Everyone
Greetings and Welcome
We hope you enjoy this
Square of 5 is 25
```

Functions can be explained in any of the following ways

* **Functions are a group of statements, that perform a particular task, bundled together under a single name**
* **Functions are mechanisms that can accept data, transform it and return something**

Functions provide a way to divide up our logic into small, easily readable and understandable blocks. This makes our programs easy to modify and maintain. 

A huge part of software engineering is communication. If your code can effectively commiunicate what it is trying to do, other engineers can quickly fix errors, add new features and perform optimizations.

Let's talk about defining functions.


## Defining Functions

The general footprint of a function in C is the following

```C
return-type function_name(datatype argument1, datatype argument2, ...) {
	// function body
}
```

* **return-type** can either be `void` or any of the valid data typea, including structures
* **function-name** follows the same rules that we use to declare variable names
* **argument1, argument2, ...** are the inputs to the function, these variables are available in the function body

to explain the `square()` function used previously, we defined

```C
int square(int x){
	int answer = x*x;
	return answer;
}
```

1. a function that returns an integer
2. it has the name "square"
3. it takes an integer as input, we name the argument variable `x`
4. in the function body, we multiply `x` with itself and store it `answer`
5. we return `answer` which is of type integer.

Some examples of functions

```C
// TODO add more examples of functions here

int greater(int a, int b){
	if(a > b) {
		return a;
	}
	else {
		return b;
	}
}
```

### Function Prototypes


## Arguments and Return Types

// TODO add a graphic here to show arguments and returns


Arguments are the values we pass to the function when we call it, the `x` in `int square(int x)` is an argument. We can also think of arguments as input data we provide the function to process. 

We can place any number of arguments of any type when we define our functions. We just have to make sure that the correct number of arguments are passed when calling the function.

```C
#include <stdio.h>

void printNumber(int a, int b){
	printf("%i %i\n", a, b);
}

int main(){
	printNumber(3); // this will cause an error
	return 0;
}
```

If we try to compile this, we will get an error as such

```shell
$ gcc functions.c
test.c: In function ‘main’:
test.c:8:2: error: too few arguments to function ‘printNumber’
    8 |  printNumber(3); // this will cause an error
      |  ^~~~~~~~~~~
test.c:3:6: note: declared here
    3 | void printNumber(int a, int b){
      |   
```


## Local and Global Variables

The definitions of local and global variables are simple, variables that are accessible throughout the program in all the functions are called **global variables**. 

Variables only accessible in their parent scope i.e their parent function, for loop etc. are called **local variables**

```C
#include <stdio.h>

const float pi = 3.14159; // global variable

double area_of_circle(double r) {
	double area = pi * r * r; // local variable
	return area;
}

int main(){
	double r; // local variable
	printf("Enter radius: ");
	scanf("%f", &r);

	printf("The value of pi = %f\n", pi);
	printf("The area of circle is %f\n", area_of_circle(r));
	return 0;
}
```

```shell
$ ./a.out
Enter radius: 15
The value of pi = 3.141590
The area of circle is 706.857777
```


## Scope and Lifetime of Variables

By default all variables are local in nature, they are only accessible in the block they are declared in. The block in which a particular variable is accessible is known as the **scope** of the variable.

When we say "the variable went out of scope" we mean to say that the program was done executing that block of code and the variables in that scope are no longer accessible. In fact variables are deleted from the memory when they go out of scope, there are keywords we can use while declaring variables to change this deletion mechanism. One of them is `static` as we will view in the next section.


## `static` Variables

When we declare variables, what we are actually doing is we are declaring `auto` variables, its default behaviour. `int a` is the same as `auto int a`.

What `auto` means is that, "delete this variable from memory as soon as it goes out of scope". This is what gives the variables a local nature by default.

If you place they keyword `static` in place of `auto`, you enter a totally different game. The word `static` means stationary, referring to no movement, and thats exactly what happens to variables when we declare them `static`.

`static` variables are not deleted from the memory when they go out of scope. 

This is the key to the concept of a static variable—it does not come and go as the function is called and returns. This implies that
the value a static variable has upon leaving a function is the same value that variable will have the next time the function is called. Static variables are removed from the memory only when the entire program ends. Its life cycle is the same as that of the entire program.

Static variables also differ with respect to their initialization. 

A static, local variable is initialized only once at the start of overall program execution—and not each time that the function is called. Furthermore, the initial value specified for a static variable must be a simple constant or constant expression. Static variables also have default initial values of zero, unlike automatic variables, which have no default initial value.

Let's look at an example

```C
#include <stdio.h>

void static_add(){
	static int a = 1;
	printf("%i\n", a);
	++a;
}

void add(){
	int a = 1;
	printf("%i\n", a);
	++a;
}


int main(){
	printf("Running add()\n");
	for(int i=0; i<5; i++){
		add();
	}

	printf("Running static_add()\n");
	for(int i=0; i<5; i++){
		static_add();
	}

	return 0;
}
```

The output will be

```shell
$ ./a.out
Running add()
1
1
1
1
1
Running static_add()
1
2
3
4
5
```

As you can see, 

* The `add()` function worked normally, it initialized `a` and printed it, incremented it, and `a` went out of scope after the function was one
* `static_add()` totally ignored the initialization in the further calls because it was not removed from the scope when the function call ended, it kept incrementing `a` and thus we got the following output.


## `static` Functions

Static functions are pretty simple, functions declared static become isolated to that particular source file. So if we include this source file in another one, we won't have access to the functions declared static. 

This example should clear it up

```C
// a.c
#include <stdio.h>

static void printTemperature(){
	printf("The temperature right now is 30 degrees celsius");
}

// b.c
#include <stdio.h>

int main(){
	printTemperature();
	return 0;
}
```

If we try to compile this,

```shell
$ gcc a.c b.c
b.c: In function ‘main’:
b.c:4:2: warning: implicit declaration of function ‘printTemperature’ [-Wimplicit-function-declaration]
    4 |  printTemperature();
      |  ^~~~~~~~~~~~~~~~
/usr/bin/ld: /tmp/ccqhFKCh.o: in function `main':
b.c:(.text+0xe): undefined reference to 'printTemperature'
collect2: error: ld returned 1 exit status
```

`undefined reference to 'printTemperature'`, thats the main error, the linker could not find the `printTemperature` function because it was declared static and was isolated only to the `a.c` file.


## Arrays and Functions



## Recursive Functions

Let's talk about Recursion. It is one of the most fascinating concepts in programming, yet the most misunderstood and dreaded topic among the students especially here in KIIT.

**Recursion is a process in which a function calls itself.** That's pretty much it for the definition of recursion. 

We use recursion to solve problems whose solution depends on the solutions of smaller instances of the same problem. 

For example the Fibonacci series,

$$0,1,1,2,3,5,8,13,21,34...$$

**The nth fibonacci number is the sum of the previous 2 fibonacci numbers**, and the first 2 fibonacci numbers are 0 and 1. 

$$fib(n) = fib(n-1) + fib(n-2) \space \space \space \space \forall \space n>2$$
$$fib(1) = 0  \space \space \space \space fib(2) = 1$$

If you think about it, the whole formula becomes pointless if we don't provide the condition that the first 2 fibonacci numbers are 0 and 1. This is what we call the **base condition** in recursion. The formula given above is called a recurrence relation.

If we had to write that recurrence relation in code. We could write it this way,

```C
int fibonacci(int n){
	return fibonacci(n-1) + fibonacci(n-2);
}
```

But there is one problem with this code, if we call it, it will never stop, it will keep running for ever as it will


