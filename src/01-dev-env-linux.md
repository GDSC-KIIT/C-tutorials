# Setting up a Dev Environment in Linux

> “Just sudo it” - Linux stan

**Outline**

- Choosing a Text Editor
- The C Compiler

## Choosing a Text Editor

1. gedit is the default text editor of the GNOME desktop environment. To create a file named **hello.c** and edit that in gedit, open your terminal and type -

```bash
gedit hello.c
```

2. Vim is the text editor which you can run in the terminal itself. To create/open a file called **hello.c** , type -

```bash
vim hello.c
```

To save and exit, press <kbd>ESC</kbd> to go into **COMMAND MODE**, then type `:wq`. [Here](https://devhints.io/vim) is a cheatsheet for Vim.

3. You can use any other editor of your choice like Sublime Text, Visual Studio Code, Atom, etc. We'll be using Visual Studio Code in this series. To download it on an Ubuntu based Linux, simply go to Ubuntu Software, search for it and install. Open it and install the **C/C++ extension** by pressing <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>X</kbd> and searching for it in the Search bar. To download it from the terminal, the process is different for different Linux distros hence follow the process [here](https://code.visualstudio.com/docs/setup/linux)

## The C Compiler

For this, we will be using GCC which is used to compile C and C++ code.

1. First, check if you already have gcc by firing up your terminal and typing -

```bash
gcc -v
```

2. If **Command gcc not found** pops up instead of a version number, type -

```bash
sudo apt install gcc
```

And with this, we're done with setting up a development environment with C in Linux.
