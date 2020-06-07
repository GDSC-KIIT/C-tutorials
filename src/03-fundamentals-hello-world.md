# Fundamentals and Hello World

> "You don't have to be great to start, but you have to start to be great." - Joe Sabah

**Outline**

- A simple "Hello World" program
- Compiling and Running
- Explanation of the Program


## A simple "Hello World" program

1. Open a new file in your code editor, name it `hello-world.c`
2. Don't forget the `.c` extension, thats how we recognize C programs
3. Add the following code in the file and save.

```C
// prints "Hello, World!" on the screen

#include <stdio.h>

int main(){
	printf("Hello, World!\n");
	return 0;
}
```


## Compiling and Running

If you have setup your compiler properly, the `gcc` command must be available in your terminal. 
Navigate to the directory where you have your `hello-world.c` file stored and run the following in your terminal.

```shell
$ gcc hello-world.c
```

Running this should compile the program and generate a file named `a.out`. This is the executable binary generated from the
C code we gave to the compiler. Now to run this file, do the following

```shell
$ ./a.out
```

and you will see an output like this, 
```shell
$ ./a.out
Hello, World!
$
```

Yay, you just successfully ran your first C program.


## Explanation of the Program

Now let's comb through the code and try to understand what we did we do exactly.

```C
#include <stdio.h>

int main(){
	printf("Hello, World!\n");
	return 0;
}
```

<br>


`#include <stdio.h>`

This line of code "includes" the `stdio.h` header file, its short for standard input output. It has a lot of functions
that we can use to input and output stuff on the terminal. 


`int main(){ ... }`

This is the `main` function. This is the first block of code that is executed when we run the program. The `int` 
placed there implies that the main function returns an integer. If you are confused by what a function is, don't worry 
functions will be discussed in detail in later chapters


`printf("Hello, World!\n");`

This is the line of code responsible for printing the text "Hello, World!" on the screen, the `\n` prints a new line 
after the text. This function is defined in the `stdio.h` header file we just included on the first line.


`return 0;`

Remember the `int` in `int main(){ ... }` ? 

This line returns 0 because the main function has to return a integer. It also means that the program ended successfully
without any errors. 

## Next Steps

Try printing various other texts like your name, your favourite colour etc.