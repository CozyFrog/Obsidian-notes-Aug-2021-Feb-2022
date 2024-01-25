Basic IO in C
- Implicit streams (STDIN/STDOUT)
	- getchar/putchar
- Explicit streams:
	- getc / putc
	- fgetc / fputc
- Formatted output
	- print3
	- scanf

- Standard files
	- Three of tem
		- stdin (=0)
		- stdout	(=1)
		- stderr (=2)
- Standard APIs to access standard files
	- Two of them
		- Unbuffered (open/close/read/write) //Uses file descriptors
		- Buffered (fopen/fclose/fread/fwrite) //Uses file pointers


You can have multiple processes executing concurrently at any one point in time (process is an address space)

Line between user land and kernel land.

File descriptor table (FDT) - every process has one of these in Kernel Land.
Entries are numbers, which are references to files that are currently open to what the operating system needs to maintain in order to give you access to these files.
Pointer (number) to object that is basically a file (file could even be devices like keyboard, display).

Three file descriptors:
0: stdin
1: stdout
2: stderr

by default 0 is bound to keyboard, 1 refers to the display, and 2 refers to wherever we want to put the errors (could be log, could be display too)



# getchar/putchar
Implicit because you don't get to specify which stream you're dealing with (hardcoded)
- int getchar(void)
	- reads a char from STDIN
	- returns the character just read in
- int putchar(int)
	- write the char received as argument on STDOUT
	- returns the char that was just written out

# getc/putc
EXPLICIT
same as getchar/putchar, but you get to provide the stream
all you need is an IO stream
- you get with fopen
- close with fclose
differences?
one is a macro (putc) the other is a function (fputc)

3 global variables that are of type FILE*:
- stdin
- stdout
- stderr

just use fgetc, fputc

# Opening streams
fopen
- give the filename
- give a string to indicate
- "r" reading mode
- "r+" read and write
- "w" writing mode
- "w+" read and write but file is created or truncated
- "a" write, the file is created if it does not exist


$\\$
$\\$


# Debugging
Add -g to cc command

- GDB
	- Simple CLI
	- No GUI

Heisenbugs are the worst
- When you add instrumentation to find the bug, it hides 

- Process:
	- Reproduce
	- Isolate
	- Formulate Hypothesis
	- Test Hypothesis
	- Fix

- Debugging is an iterative process 
	- First find the smallest condition that always tirggers it
		- smallest conceivable input, test program
		-
		
- Reproduce
- don't hesitate to change the program to
	- hard code the input
	- hard code intermediate results that get rid of irrelevant paths
	- eliminate all UI 
	- smaller code, better!

- Isolate
	- what is the sympomatic cause? NOT the underlying cause

$\\$
$\\$

# Compiler and Linker
- Compilation Workflow
	- source1.c (input) ->
	- Visible Compiler:
		- Macro Pre-processor ->
			- header1.h, header2.h, etc. (input)
		- "true" source buffer ->
		- C compiler ->
		- Assembly ->
		- Assembler ->
	- Object File (output) (.o)

- Pre-processor
	- carries out macro expansion, automatic replacement is sent to compiler
- Compiler
	- takes c file, produces assembly
- Assembler
	- takes assembly file, produces object code to be glued together with lib. files by the linker
- Overall, four steps:
	- cc Preprocess (-E, -c), .c
	- cc Compile (-S), .s
	- as Assemble (-c), .o
	- cc Link

$\\$
$\\$

# Linker
- Purpose
	- Pull together the object files and libraries
		- .o, .o, .o, .a

- Automation with Makefile
	- define collection of variables
		- arguments, options
	- define collection of rules
		- dependencies

target : dependencies
$\quad$command

rebuild target whenever any dependencies change
example:

OFILES = stack.o stacktest.o
CFLAGS = -g
all: stacktest
stacktest: \$(OFILES)
$\quad$\$(CC) \$(OFILES) -o \$@ // \$@ is the name of the target

stack.o: stack.c
$\quad$\$(CC) -c \$(CFLAGS) \$< // \$< evaluates to the first dependency (so stack.c)

stacktest.o: stacktest.c
$\quad$\$(CC) -c \$(CFLAGS) \$<

clean:
$\quad$rm -rf \*.o \*-

// \$^ entire list of dependencies
// %.o : %.c // any .o can be derived from the corresponding .c