# Functions

**Outline**
* What are Functions ?
* Defining Functions ?
* Arguments and Return Types
* Local and Global Variables
* Scope and Lifetime of Variables
* `static` Variables
* `static` Functions
* Variable Length Arrays and Functions
* Recursive Functions


## What are Functions ?

Functions are the building blocks of large programs in C. 

When you hear functions, you probably think of functions as we learn them in math, functions in C work in a similar way, there are multiple ways to think of functions and each one of them offers a unique perspective into the role of functions. 

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

* Functions are a group of statements, that perform a particular task, bundled together under a single name
* Functions are mechanisms that can accept data, transform it and return something

Functions provide a way to divide up our logic into small, easily readable and understandable blocks. This makes our programs easy to modify and maintain. 

A huge part of software engineering is communication. If your code can effectively commiunicate what it is trying to do, other engineers can quickly fix errors, add new features and perform optimizations.



## Defining Functions ?



## Arguments and Return Types



## Local and Global Variables



## Scope and Lifetime of Variables



## `static` Variables



## `static` Functions



## Variable Length Arrays and Functions



## Recursive Functions



