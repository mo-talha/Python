# Python Notes
**print() function**
The print function can take in multiple strings and multiple data types at once and prints them separating with a space.
Ex: print(“talha”) → talha, print(“talha”, “yaseen”, “taha”), print(“talha”, 25, “yaseen”, 21, 44) all these are valid.

**The print function can take the following arguments:**
A separator: By default it's a space, but we can change this to anything of our choice like ‘-’, ‘/’ etc. ex: print(“talha”, 25,sep=‘:’) → this will print talha:25
end: we can define where the line should start after printing something, by default it is set to new line or ‘\n’

## Data types
1. Basic types: int, float, complex, boolean, string
2. Container types: list, tuple, set and dictionary
3. User defined types: classes

int can store any integer upto 10^308, basically this means the number 1 can be followed by 308 zeros, after this will be infinity.

float can store decimal numbers like 1.2, 4.5 etc and its range is also huge 1.7e308 i.e. 1.7 * 10^308, it is 170 followed by 308 zeros

Boolean in python is True or False

String in python can be written in single inverted commas(‘ ’), double inverted commas(“”) and also triple inverted commas(“”” ”””), there is no different type for a char in python.

Java has a limit for every primitive data type like int, float, double, long etc

Container types are used to store data of different types, lists are the same as arrays in java but here it can store multiple types in it, unlike java where an array can store data of only a single type.
- Tuple is the same as a list.
- Set is used to store unique elements, it will not store duplicates
- Dictionary is used to store key value pairs.

## Variables in python:
Variables are containers for future use. Ex: we design 
In python there is no declaration of variables like in other languages like java where we declare a variable like int num = 4. Here, we are specifying the data type of variable num, but this is not required in python, we can just write num = 4 and the python runtime will recognize this as a num/integer.

Also declaring the type before a variable is called static typing and not declaring is called dynamic typing.

In python the data types are interpreted during runtime.

## Dynamic Binding
In python the variables can change data types, i.e. if a variable name is initialized with a string ex: name = ‘taz’, then we can reinitialize it to name = 2 an integer type.

But in Java/C this is not possible if a variable is of type int, then it can only be re-initialized with a type int, this is called static binding.

So, basically in python the data of a variable can keep changing.

**Different ways of declaring variables in python**
a=1;b=2;c=3 → multiple variables in a single line.
a,b,c = 1, 2, 3 → multiple variables and their values separated by commas
a=b=c = 3 → all three a, b and c will have its value as 3

## How python code is executed
Python is an interpreted language, i.e. the code is first converted into byte code by the compiler and the PVM (python virtual machine) interprets the bytecode to machine code.

Ex: A mediator b/w two people speaking russian and english, the mediator understands/interprets russian and passes on to the english person, he first hears then conveys.
Similarly the interpreter interprets a line and then processes it to machine code and runs it.

Unlike Java, which is a compiled language, it gets compiled to bytecode by the compiler first fully and then the bytecode is converted to machine code by jdk/jit at runtime.

**CPython is the reference implementation of Python. When you run a module:
It consists of a Parser, a Compiler and a Runtime and many other things like the standard library.**

- Parse → AST (tree of syntax nodes).

- Compile → bytecode packed into code objects (module code object plus one for each function/class/comprehension).

- Execute those bytecode instructions in the CPython virtual machine (an interpreter written in C).

- The module’s bytecode may be cached as a .pyc in __pycache__ for faster future imports.

**In Short: Python (CPython) compiles source to bytecode and the CPython VM interprets that bytecode. So CPython has both the compiler and the interpreter. 
A language like C is directly compiled to machine code hence it is faster, it skips the step of interpretation.**

**Simplified view of CPython architecture:**
CPython = {
    "Parser":       "Converts source to AST",
    "Compiler":     "AST → Bytecode (.pyc files)",
    "Interpreter":  "Bytecode → Execution (C VM)",
    "Memory Mgmt":  "Reference counting + GC",
    "Standard Lib": "Batteries included",
    "C API":        "Interface for C extensions"
}

There are other runtimes to run python code other than CPython, one is PyPy it is does the same steps as CPython but it has a JIT compiler which hot codes any repetitive code to machine code to avoid re interpreting the same code again and again.
`PyPy = {
    "RPython Toolchain": "Translates RPython → C",
    "Python Interpreter": "Written in RPython",
    "JIT Compiler":       "Runtime optimization",
    "GC":                 "Different garbage collector",
    "Compatibility":      "cpyext for C extensions"
}`



