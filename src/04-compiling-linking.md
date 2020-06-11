# Compiling and Linking

> Understanding the behind the scenes of compiling C programs and running them.

**Outline**

- What is a Compiler ?
- Compiling, Assembling and Linking


## What is a Compiler ?

Computers are dumb, the reason why they are called dumb is because we humans have to instruct computers down to the very last bit so that they perform the calculations we want them to. A computer will do exactly what you say it and nothing more. Programming is nothing but the act of this "instruction". Programming is when we humans write up the instructions and feed it to the computer in a proper format so that the computer can accordingly get it's dumb processor to work. 

Computers do not understand english, or as a matter of fact any natural language we humans use. Computers are electronic devices made out of silicon and copper, they run on electricity. The fundamental operations of a computer run on 2 kinds of electrical signals / impulses, a HIGH voltage (represented as 1) and a LOW voltage (represented as 0). 

To program a computer, you have to pass in a huge sequence of 0s and 1s, this is also known as Binary Code or Machine Code. When the computing industry had just started, computer scientists used to write out these entire sequences by hand which obviously was a very tedious job to do and was prone to a lot of errors. Thus they developed tools to make this whole process easier. 

Programming langauges and compilers were built to solve this exact problem. The task at hand was to somehow convert code that humans could read to code that machines could read and work with i.e Machine Code. And that is exactly what a compiler is, it's a piece of software that converts code that follows a particular specification into machine code. When we refer to a "Programming Language" we usually mean the specification of how the code should be written by us programmers so that the compilers can convert it efficiently to machine code. 

C is a programming language and the compiler we are using is `gcc` which is short for the **GNU C Compiler**. There are a lot of other compilers for C. The most famous ones are `gcc` and `clang`, you can google them up if you're curious. 

When we run, 

```shell
$ gcc hello-world.c
```

All `gcc` does is that it converts our files with a `.c` extension to a machine code equivalent of the current opeating system, which is `.out` files in Linux and `.exe` files in Windows


Now, if you're curious regarding what exactly happens behind the scenes to our `hello-world.c` file then keep reading on. Or else feel free to skip to the next chapter :-)

## Compiling, Assembling and Linking

The whole process of getting from `.c` to `.out` is generally called **Compilation** and it's an overall 3 step process.

1. Compiling
2. Assembling
3. Linking 

* **Compiling** : In short, it converts your C code to assembly code. Assembly Language is another low level language specification that in the earlier days was very processor dependent, so every processor had it's own flavour of assembly, but now it has standardized to **x86** assembly which almost all 32 bit and 64 bit Intel and AMD processors follow.

* **Assembling** : In this part of the process, the assembly language code is converted into an Object File, it usually has the `.o` extension. The content of these object files is mostly binary code. Each source file of in C is converted to a single object file. When we start working on huge projects that have multiple files, the compiler produces an object file every single one of the `.c` files

* **Linking** : This is where all those object files are linked together to form one final binary file i.e the `a.out` or the `a.exe` file.

You can actually watch the whole process unfold by using specific flags with the `gcc` command

### Compile `hello-world.c`

```shell
$ gcc -S hello-world.c
```

Running the above command will just compile the `hello-world.c` file, it will put the assembly language code in a file named `hello-world.s`


This is what x86 assembly stored in `hello-world.s` looks like

```shell
$ cat hello-world.s
	.file	"hello-world.c"
	.text
	.section	.rodata
.LC0:
	.string	"Hello, World!"
	.text
	.globl	main
	.type	main, @function
main:
.LFB0:
	.cfi_startproc
	endbr64
	pushq	%rbp
	.cfi_def_cfa_offset 16
	.cfi_offset 6, -16
	movq	%rsp, %rbp
	.cfi_def_cfa_register 6
	leaq	.LC0(%rip), %rdi
	call	puts@PLT
	movl	$0, %eax
	popq	%rbp
	.cfi_def_cfa 7, 8
	ret
	.cfi_endproc
.LFE0:
	.size	main, .-main
	.ident	"GCC: (Ubuntu 9.3.0-10ubuntu2) 9.3.0"
	.section	.note.GNU-stack,"",@progbits
	.section	.note.gnu.property,"a"
	.align 8
	.long	 1f - 0f
	.long	 4f - 1f
	.long	 5
0:
	.string	 "GNU"
1:
	.align 8
	.long	 0xc0000002
	.long	 3f - 2f
2:
	.long	 0x3
3:
	.align 8
4:
```

Now let's move on to assembling our program

### Assembling `hello-world.c`

```shell
$ gcc -c hello-world.c
```

Running the above mentioned command will compile and assemble the file, it will generate an object file named `hello-world.o`. If we try to view the contents of `hello-world.o` file using some standard command like `vim` or `cat` we will end up looking at something very gibberish characters, and that makes sense because the object files are not out regular ASCII text files. 

The `file` command tells us the type of file we pass.

```shell
$ file hello-world.o
hello-world.o: ELF 64-bit LSB relocatable, x86-64, version 1 (SYSV), not stripped
```

We can use a command called `hexdump` to view  `.o` files in our terminal. To be more specific `hexdump` stands for hexadecimal dump, it gives the hexadecimal output of the given data. It's okay if you don't understand what hexadecimal is, it will be explained in later chapters.

```shell
$ hexdump hello-world.o
0000000 457f 464c 0102 0001 0000 0000 0000 0000
0000010 0001 003e 0001 0000 0000 0000 0000 0000
0000020 0000 0000 0000 0000 0310 0000 0000 0000
0000030 0000 0000 0040 0000 0000 0040 000e 000d
0000040 0ff3 fa1e 4855 e589 8d48 003d 0000 e800
0000050 0000 0000 00b8 0000 5d00 48c3 6c65 6f6c
0000060 202c 6f57 6c72 2164 0000 4347 3a43 2820
0000070 6255 6e75 7574 3920 332e 302e 312d 7530
0000080 7562 746e 3275 2029 2e39 2e33 0030 0000
0000090 0004 0000 0010 0000 0005 0000 4e47 0055
00000a0 0002 c000 0004 0000 0003 0000 0000 0000
00000b0 0014 0000 0000 0000 7a01 0052 7801 0110
00000c0 0c1b 0807 0190 0000 001c 0000 001c 0000
00000d0 0000 0000 001b 0000 4500 100e 0286 0d43
00000e0 5206 070c 0008 0000 0000 0000 0000 0000
00000f0 0000 0000 0000 0000 0000 0000 0000 0000
0000100 0001 0000 0004 fff1 0000 0000 0000 0000
0000110 0000 0000 0000 0000 0000 0000 0003 0001
0000120 0000 0000 0000 0000 0000 0000 0000 0000
0000130 0000 0000 0003 0003 0000 0000 0000 0000
0000140 0000 0000 0000 0000 0000 0000 0003 0004
0000150 0000 0000 0000 0000 0000 0000 0000 0000
0000160 0000 0000 0003 0005 0000 0000 0000 0000
0000170 0000 0000 0000 0000 0000 0000 0003 0007
0000180 0000 0000 0000 0000 0000 0000 0000 0000
0000190 0000 0000 0003 0008 0000 0000 0000 0000
...
```

That's what machine code looks like pretty much. This is what goes into the processor and we get our output.

### Linking

```shell
$ gcc hello-world.c
```

Finally to run all the steps in one go we use the regular command and get our `a.out` file. It combines the `.o` files and links them together to create one final execuatble binary.

```shell
$ file a.out
a.out: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), 
dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, 
BuildID[sha1]=cbfd7a9a8c122f654ad693ea9e59a41df7cf77f1, 
for GNU/Linux 3.2.0, not stripped

$ hexdump a.out
0000000 457f 464c 0102 0001 0000 0000 0000 0000
0000010 0003 003e 0001 0000 1060 0000 0000 0000
0000020 0040 0000 0000 0000 3978 0000 0000 0000
0000030 0000 0000 0040 0038 000d 0040 001f 001e
0000040 0006 0000 0004 0000 0040 0000 0000 0000
0000050 0040 0000 0000 0000 0040 0000 0000 0000
0000060 02d8 0000 0000 0000 02d8 0000 0000 0000
0000070 0008 0000 0000 0000 0003 0000 0004 0000
0000080 0318 0000 0000 0000 0318 0000 0000 0000
0000090 0318 0000 0000 0000 001c 0000 0000 0000
00000a0 001c 0000 0000 0000 0001 0000 0000 0000
00000b0 0001 0000 0004 0000 0000 0000 0000 0000
00000c0 0000 0000 0000 0000 0000 0000 0000 0000
00000d0 05f8 0000 0000 0000 05f8 0000 0000 0000
00000e0 1000 0000 0000 0000 0001 0000 0005 0000
00000f0 1000 0000 0000 0000 1000 0000 0000 0000
0000100 1000 0000 0000 0000 01f5 0000 0000 0000
0000110 01f5 0000 0000 0000 1000 0000 0000 0000
0000120 0001 0000 0004 0000 2000 0000 0000 0000
0000130 2000 0000 0000 0000 2000 0000 0000 0000
0000140 0160 0000 0000 0000 0160 0000 0000 0000
0000150 1000 0000 0000 0000 0001 0000 0006 0000
0000160 2db8 0000 0000 0000 3db8 0000 0000 0000
0000170 3db8 0000 0000 0000 0258 0000 0000 0000
0000180 0260 0000 0000 0000 1000 0000 0000 0000
0000190 0002 0000 0006 0000 2dc8 0000 0000 0000
00001a0 3dc8 0000 0000 0000 3dc8 0000 0000 0000
...
```

**NOTE** : The actual `hexdump` outputs are very large, the `...` are used to skip a major part of it.

### Too much, right ?

It is okay if you did not understand all of what was going on in this chapter, it is pretty overwhelming for beginners to be honest, but as you write more code and get more used to C, you can come back to this chapter again and it will definitely help you connect the dots regarding what's actually happening with your code.





