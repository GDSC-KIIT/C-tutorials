# Setting up a Dev Environment in Windows

> “Let's jump into it!” - Anonymous

**Outline**

- Choosing a Text Editor
- The C Compiler

## Choosing a Text Editor

We'll use Visual Studio Code as our default text editor because it's simple, powerful and was made for Windows. But feel free to use any other text editor like Sublime Text, Atom, etc. We have instructions for both.

To set up Visual Studio Code on Windows -

1. Download and install it from [here](https://code.visualstudio.com/).
2. Navigate to a folder where you want to save your C programs (for ex - C drive) and create a new folder (my folder's name c-programs).
3. Open Command Prompt and move into that folder with `cd`.

```
cd c-programs
```

4.  To open Visual Studio Code in that folder type -

```
code .
```

5. You'll be greeted by an empty folder. Let's create a C file with <kbd>ctrl</kbd> + <kbd>N</kbd> and renaming it to **test.c**.
6. Several extensions will pop up for C but if they don't, simply <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>X</kbd> to open the Extensions sidebar and search for C/C++. It allows line completion, simple debugging and code browsing. Install it once you find it.

7. Search for the Code Runner extension to run our C programs in the VS Code terminal itself and install it.

8. Now type this simple C code in **test.c** that prints **Hello World** (don't worry about the syntax, we'll explain everything in detail later) -

```C
#include <stdio.h>

int main(){
    printf("Hello World");
    return 0;
}
```

9. Do <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>N</kbd> to run this code and a terminal will pop up and might show this error -

```
gcc is not recognized as an internal or external command
```

If it doesn't and shows **Hello World** instead, it means, you already have a C compiler. You don't need to follow the steps below.

If you're using any other text editor -

1. Follow steps **2** and **3** from above.
2. Then create a file called **test.c** and write the code in step **8** and save it.

Once we download the C compiler, I'll show you how we can run the C programs from Command Prompt. This is applicable for people who are not using VS Code.

## The C Compiler

We wanted our program to print **Hello World**, instead got an error. To overcome this, we need a compiler. We'll discuss more on what it is in the later chapters but for now let's just see how we can set one up in Windows. We will be using the TDM-GCC compiler.

The following steps are common for all people -

1. Download the installer from [here](https://sourceforge.net/projects/tdm-gcc/).
2. Choose **Create** a new TDM-GCC installation.
3. Go with the defaults but remember to keep note of the folder where you installed TDM-GCC. Finally, click on **Install**.
4. Navigate to the folder where you installed TDM-GCC and go inside **bin**. Now copy this path. Mine looks like this - C:\TDM-GCC-64\bin
5. Now in your **Search Box**, search for **Edit environment variables for your account**.
6. Select **Path** and click on **Edit**.
7. Click on **New** and paste the path we just copied. Click on **OK** and we're done.

Now, for VS Code users, restart VS Code and run the the **test.c** program again. We'll get the output "Hello World" in the terminal.

For all other text editors, we'll run **test.c** in Command Prompt. The steps are -

1. Open Command Prompt and navigate to the folder where **test.c** is saved.
2. Type in -

```
gcc test.c
```

This compiles the file and stores the output in an executable file called **a.exe**

3. To view this output, we simply type in -

```
./a.out
```

4. And voila! We get the output "Hello World".
   If you want to give the output a specific name (for example - testOutput) and then print the output, the commands are -

```
gcc -o testOutput test.c
./testOutput
```

And with this, we're done with setting up a development environment with C in Windows.
