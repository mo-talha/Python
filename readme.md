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

float can store decimal numbers like 1.2, 4.5 etc and its range is also huge 1.7e308 i.e. 1.7 \* 10^308, it is 170 followed by 308 zeros

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

- The module’s bytecode may be cached as a .pyc in **pycache** for faster future imports.

**In Short: Python (CPython) compiles source to bytecode and the CPython VM interprets that bytecode. So CPython has both the compiler and the interpreter.
A language like C is directly compiled to machine code hence it is faster, it skips the step of interpretation.**

**Simplified view of CPython architecture:**

```
CPython = {
    "Parser":       "Converts source to AST",
    "Compiler":     "AST → Bytecode (.pyc files)",
    "Interpreter":  "Bytecode → Execution (C VM)",
    "Memory Mgmt":  "Reference counting + GC",
    "Standard Lib": "Batteries included",
    "C API":        "Interface for C extensions"
}
```

**There are other runtimes to run python code other than CPython, one is PyPy it is does the same steps as CPython but it has a JIT compiler which hot codes any repetitive code to machine code to avoid re interpreting the same code again and again.**

```
PyPy = {
    "RPython Toolchain": "Translates RPython → C",
    "Python Interpreter": "Written in RPython",
    "JIT Compiler":       "Runtime optimization",
    "GC":                 "Different garbage collector",
    "Compatibility":      "cpyext for C extensions"
}
```

**Points to remember:**
The python virtual machine CPython has both compiler and interpreter. The source code is
compiled to bytecode by the compiler then the interpreter executes the bytecode.

- Python, Java is a compiled and interpreted language.
- C, Rust and Go are only compiled languages, i.e. their compiler directly compiles the source code to machine code no bytecode.

## Keywords:
Keywords are reserved words, these words cannot be used as variable names, function names etc in a program. Keywords cannot be changed. Ex: for, while, print etc
There are 33 keywords in python.

## Identifiers:
Identifiers are names used to identify a variable, function, class, module or an object.
Rules for naming identifiers:
Can only start with an alphabet or an _.
Followed by 0 or more letters, _ and digits
Keywords cannot be used as identifiers.

Python is a case sensitive language, it means there will always be difference b/w false and False as **False** is a keyword.

## Lecture - 6
**What is the input method ?**
input() method, this is used to take input from the user. It takes in an argument called prompt.
Ex: input(prompt=“Your name”)/input(“Your name”) → this will print Your name on the console and give a blinking cursor to the user.

Also the input method takes prompt as a string, so even if we enter int, float etc it will consider it as a string.
Ex: If we write a program to add two numbers by taking the user input
num_1 = input(“Enter the first number: ”)
num_2 = input(“Enter the second number: ”)
print(num_1 + num_2)
When user enters numbers 1 and 2 in the console, the print function will print 12, since the prompt takes in a string and string is a universal type in python i.e. any data type can be stored as a string but not the vice versa, 
So instead of printing 1+2 = 3 it is giving 12 because since both num_1 and num_2 are prompts which are strings a string concatenation takes place.

## Lecture - 7
Type Conversion
- There are two types of type conversions in python
- Implicit conversion
- Explicit conversion 

**Implicit Conversion**
This conversion is done by python without specifying. Ex: 2 + 4.5 = 6.5, here an int is added with a float, python automatically gives a floating result.

**Explicit Conversion**
Every data type has a type conversion method in python.
Ex: int(4.5) → this will give 4, similarly, float(3) → 3.0, str(4) → ‘4’

**Note:** Also type conversion is not permanent i.e. if a = ‘3’, int(a) → this will give 3 but if we print a it will still be string ‘3’. Hence a conversion method returns a new value, i.e. int(a) will give a new value 3 which can be stored in another variable.

## Lecture-8
Literal is a value given to a variable. Ex: num = 2, here 2 is a literal, name = ‘taz’ here taz is a literal.

In python we have 4 types of literal, numeric literals, string literals, boolean literals and special literals.

### None in python
We know that we cannot simply declare a variable in python without a literal, this is where we can None.

None is used to specify that there is no value or simply nothing. Similar to null in Java.
In Java this is possible int x; without specifying a literal like 0 or 1 etc. This is possible because internally int’s value is 0.

In python this is not the case, we cannot just leave it like x or num etc hence we do 
num = None.

## Lecture-9
Operators in python
### Arithmetic Operators:
1. +, used to add numbers
2. -, used to subtract two numbers
3. /, used to divide two numbers, gives a floating value, ex: print(5/2) → gives 2.5
4. %, gives the remainder of a division
5. *, used to multiply two numbers
6. //, integer division operator, gives out an integer value after a division. print(5//2) → prints 2
7. **, it used to calculate n power x, ex: 5 ** 2 = 25, it basically means 5 power 2.

### Comparison Operators:
1. `>` - used to check if a > b
2. < - used to check if a < b
3. `>=` : used to check if a > or = b
4. <= : used to check if a < or = b
5. == : used to check if a == b
6. != : used to check if a != b

### Logical Operators:
1. or - used to execute an operation if one among the two values is true. ex: if a = 2 or b =1 print(‘hi’)
2. and - used to execute an operation if both values are true ex: if a and b == 2 print(2);
3. not - 

### Bitwise Operators:
These operators are used and work only on binary numbers.

1. & : this is different from logical and. Ex: if we do print(2 & 3) → this gives 2.
because, 0 1 0
                1 1 1
                —----
                0 1 0 → this is the binary of 2, hence we get 2.
In & operation if any one bit among two is 0 then its result is 0, if both are 0 then it is 0 or if both bits are 1 then result is 1
| : this is bitwise or (|) unlike logical or, it is also used to perform operations b/w two binary numbers.
0 1 0
1 1 1
—---
1 1 1 → This is the binary of 3.
	In | if one digit is 1 or both digits are 1 then the ans is 1, if both digits are 0 then ans is 0.

2. `>>` : right shift and, learn about this
3. << : left shift and
4. ~ : one's complement operator.

### Assignment Operator:
1. = : this is used to assign a value to a variable, like a=1, name = ‘taz’ etc.
2. += : this is used to increment a value, ex: a += 1, it is the same as a = a + 1.
3. -= : similar as above but decrement.
4. *= : used to multiply
5. /= : used to divide a num
**a++, ++a, --a, a-- is not allowed in python to increment.**

### Identity Operator:
is : it is used to check if two values are stored in the same memory location or not, or we can also say if two different variables are addressing to the same memory location or not.
Ex: a = 1, b = 1, print(a is b) → this will print True, as both a and b are pointing to the same 1 in the memory.

a = [1, 2, 3], b = [1, 2, 3], print(a is b) → this will print false, because incase of a list even if they look identical but on every new assignment a new object is created in the memory hence b will have a different memory address to a.

Hence is used to check if two variables are addressing the same object or different ones.

### Membership Operators:
in : it is used to check if some value exists in another value. Ex: print(‘D’ in “Delhi”) this will print True.

similarly a = [1, 2, 3], print(2 in a) → True.

We can also do, (2 not in a) → this will print False.

## Lecture - 23
### String functions:
**Common functions:** These functions are available in other data structures as well like lists, tuples etc.

1. len() - gives the len of a string
2. max() - gives the max ASCII val character in a string
3. min() - gives the min ASCII val character in a string
4. sorted() - sortes the characters in a string according to the ASCII value and returns a list of separate characters of that string.
ex: msg = “dcba” → sorted(msg) gives [‘a’, ‘b’, ‘c’, ‘d’]
We can also sort a string in descending order using the reverse argument in the sorted function.
sorted(msg, reverse=True) will return a list of sorted characters in descending order according to their ASCII values.

5. capitalize() - It changes the first char of a string to capital letter. 
ex: c = “kolkata”, c.capitalize() → this will not modify c, but it will return a new copy of c whose first letter will be capital, ex: Kolkata

6. title() - It changes the first char of every word in a sentence to capital.
ex: c = “it is raining today”, c.title() will return a new string/sentence which will be
“It Is Raining Today”

7. upper() - It returns an uppercase copy of the given string.
ex: c = “kolkata”, c.upper() → will return “KOLKATA”

8. lower() - It is similar to upper, just that it returns a lowercase version of the given string.

9. swapcase() - It gives the count of a substring inside a string. 
ex: c = “kolkata”, c.count(k) → this will return 2, because there are 2 ks.

10. find() / index() - It returns the index of a character in the string. If there are many characters as the given character, then it will return its first occurrence.
ex: c = “kolkata”, c.find(k) → it will return 0.

we can also find a word, it will return the index of the first character of the word.
ex: c = “it is raining today”, c.find(“raining”) → this will return 6, r of raining is starting at index 6.

If it does not find the target word or character it will return -1.
The only difference index() has is, if it does not find the target then it will throw an error.

11. endswith()/startswith()
c = “it is raining”, c.endswith(“ing”) → this will return true, similarly startswith().

12. format()
It is used to fill blanks in a string, it can be used in many ways.
ex: 
c = “Hello my name is {} and I am {} years old”
c.format(“Talha”, 25), this will return a new string which will have talha and 25 in it in place of the curly braces.
ex: “Hello my name is Talha and I am 25 years old”

c = “Hello my name is {1} and I am {0} years old”
c.format(“Talha”, 25)
	“Hello my name is 25 and I am Talha years old”
	
	c = “Hello my name is {name} and I am {age} years old”
c.format(name = “Talha”, age = 25)
	“Hello my name is Talha and I am 25 years old”

Also, the format method can take any number of arguments, and it is not necessary that all these arguments must be used inside the sentence; we can choose only the ones which we want.

ex: 
	c = “Hello my name is {name} and I am {weight} years old”
c.format(name = “Talha”, age = 25, weight=70)
	“Hello my name is Talha and I am 70 years old”

13. split() - it splits the words in a sentence based on a given substring, a special character or space, and returns the separated words in a list.
ex: c = “192.0.22.200”, c.split(“.”) → [“192”, “0”, “22”, “200”]
If nothing is passed it will split the sentence based on space,
ex: c=“it is raining today”. c.split() → [“it”, “is”, “raining”, “today”]

14. join() - it is opposite of the split function, it joins the given words in a list based on a given separator and returns a string. 
ex: list = [“it”, “is”, “raining”, “today”]
Syntax = separator.join()
“ ”.join(list) → “it is raining today”
“/”.join(list) → “it/is/raining/today”

15. replace() - it replaces a given target with another value which should be given.
ex: c = “my name is talha”, c.replace(“talha”, “yaseen”) → it will return a string in which 
talha will be replaced by yaseen.

16. strip() - it removes the leading and trailing spaces in a string and returns a new string.
ex: c = “   talha  ”, c.strip(c) → returns “talha”

**Validation Functions** - These return boolean values.
1. isalpha() - checks if a string is only alphabets and returns true or false.
ex: c=”talha”, c.isalpha(), returns true.
2. isalnum() - checks if a string consists of words and nums.
c = “FLAT20”, c.isalnum() → true, isalpha will return false.
3. isdigit() - checks if a string is a number, if yes returns true or false.
c = “22”, c.isdigit() returns true.

## Lecture - 24
### Lists
### Difference b/w Array and List.
Array can store data of a single type. An array can only store integer or character or string, it cannot store multiple data of multiple types.

Array stores its data in a sequence in memory, this is not the case with lists, hence arrays are faster and lists are slower.

list can store data of multiple types.

### Creating a list:
l = [], l = list()

l = [1, 2, 3, 4] list store data of type int
l = [1, 2, “talha”, false] list storing data of different types.

l = list(“talha”) this will create a list, l = [“t”, “a”, “l”, “h”, “a”]

### 2D lists
l = [
	[1, 2, 3],
	[4, 5, 6]
]

Lists inside a list.

### Accessing elements of a list:
l = [1, 2, 3]
l[0] → 1
l[-1] → 3 last element of the list
l[::-1] → reversing a list [3, 2, 1]

**Lists are mutable in python, meaning they can be modified.**
ex: 
l = [1, 2, 3], l[2] = 4, now l will be [1, 2, 4]

**We can modify them via slicing as well,**
l = [1, 2, 3, 4], l[1:2] = [200, 300], now l will be [1, 200, 300, 3, 4]

One thing to notice is, it is replacing the 1st index element 2 with 200 and adds 300 to l without replacing 3. Because [1:2] means 2 the upper bound is not considered so technically we are only replacing 1 element i.e. 2 at 1st index and since our replacement array has 2 elements 200 and 300, after replacing 1 element 2 with 200 instead of ignoring 300 it adds 300 to l.

### Adding elements to a list
We have 3 functions:
1. append()
2. extend()
3. insert()

**append()** - will always add a single item at the end of a list.
ex: l = [1, 2, 3, 4]
l.append(5), now l will be [1, 2, 3, 4, 5]

l = [1, 2, 3, 4], l.append([5, 6]), l = [1, 2, 3, 4, [5, 6]] will always append a single item so it adds the whole list itself.
l.append(“goa”), l = [1, 2 ,3, 4, “goa”]

**extend()** - will always add multiple items to the end of a list. extend() only takes iterables as arguments, like lists, tuples, strings etc.
ex: l = [1, 2, 3], l.extend([4, 5]) → l = [1, 2, 3, 4, 5]
l.extend(1) **this is not possible, but l.extend(“a”) // this is possible as a string is iterable.**
l = [1, 2, 3], l.extend(“goa”) → l = [1, 2, 3, “g”, “o”, “a”]

**insert()** - this is used to add an element at a desired position
ex: l = [1, 2, 3], l.insert(index, value) 
l.insert(1, 4), l = [1, 4, 2, 3]

### Deleting From a List
We have 4 ways to delete from a list:
1. del - it is a keyword
2. remove()
3. pop()
4. clear()

del:
l = [1, 2, 3]
del l , this will remove the whole of l itself, the list won’t exist.

We can also remove a part of it, 
l = [1, 2, 3, 4, 5]
del l[1:3], it will remove the elements from 1 excluding the upper bound.
l = [1, 4, 5]

remove():
If we don’t know the index we can use remove and pass in the target, it will remove by locating its existence.
l = [1, “taz”, 2, 3]
ex: l.remove(“taz”) → l = [1, 2, 3]

pop():
It will remove the last element in a list.
l = [1, 2, 3, 4, 5]
l.pop()
l will be [1, 2, 3, 4]

clear(): It will empty the list.
l = [1, 2, 3, 4]
l.clear()
l will be []


### Operations on Lists
1. Concatenation: We can concatenate 2 lists
ex: l1 = [1, 2, 3], l2 = [4, 5, 6]
l1 + l2 will create a new list [1, 2, 3, 4, 5, 6], since it will create a new list we need to store it in a variable,
l3 = l1+l2
print(l3) → [1, 2, 3, 4, 5, 6]

2. Multiplication: we can multiply a list
ex: l1 = [1, 2, 3]
l1 * 3, it will create repeat the same list 3 times
l1 = [1, 2, 3, 1, 2, 3, 1, 2, 3]

3. Membership operator or in: It is used to check if an element exists in a list or not and also in loops
l = [1, 2, 3, 4]
print(3 in l) this will print true.

for i in l:
	print(i) this will print 1, 2, 3, and 4

### Functions on Lists:
1. len() - will return the len of a list
ex: l = [“taz”, 1, 2, 3], len(l) = 4

2. max() - will return the max elem in the list, but the list must contain numerical values only. 
ex: l = [1, 2, 3], max(l) will return 3

3. min() - returns the min number in a list of numbers.

4. sorted() - sorts a list in ascending order, we can also sort a list in descending order by passing the reverse argument = True
ex: l = [1, 3, 2, 4]
sorted(l) it will return a new list [1, 2, 3, 4]
sorted(l, reverse=True) it will return a new list [4, 3, 2, 1]

So, sorted is not a permanent operation on a list.

5. sort() - it does the same thing like sorted(), but it does not return a new list, it changes the existing list. Hence, sort is a permanent operation.
l.sort()
l.sort(reverse=True)

6. index() - it gives the element present at an index.
l = [1, 2, 3, 4], l.index(2), this will return 3.

**Functions like len(), sorted(), max(), min() are global functions, can be used on any iterable, will return a value, like sorted() will return a new list, tuple etc whichever is passed to it.**

**But methods like sort(), index() etc are specific to a class like list, x = [2, 3, 1], x.sort() will sort x in memory it won’t return a new object.**

**How does the sort() function sort a list of lists ?**
Ex: temp_list = [[1, 3, 2], [1, 2, 3], [2, 3, 1], [2, 1, 3]]
temp_list.sort()
print(temp_list) → [[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1]]

It does this using lexicographical order.

**Problems:**
1. turn a sentence into title without using title
def title1(s:str):
    l = s.split()
    
    newL = []
    for i in l:
        newL.append(i.capitalize())
    
    return " ".join(newL)
    
s = "is it sunday tomorrow"
newL = title1(s)
print(titles)

2. Return the name from an email
We first find the @ character in the string
Then we will slice the string from 1st to @’s index
return s[0: s.find(@)]

## Lecture - 25
### Tuples
They are same as lists but with slight differences

### Creating a Tuple:
t = ()
t = tuple()
t = (1, 2, 3)
t = ([1, 2, 3, 4])

All the above will create a tuple,

**t = (1), creating a tuple with a single item, will not create a tuple unless we use a comma after the single element.**
So, t =(1,) will create a tuple, similarly, t = (“taz”, )

### Accessing Elements in a Tuple:
t = (1, 2, 3, 4)
t[0]
we can also access via slicing, t[0:2], the upper bound will be excluded

t[-1] , will give the last elem


### Modifying/Editing a Tuple:
This is not possible because unlike list, tuple is immutable i.e. once a tuple is created it cannot be modified, we cannot add or delete elements from a tuple. 
Similar to Strings, strings are also immutable. 
s = “talha”, 
s+”mohammed”
print(s) → this will print “talha” only, because strings are immutable, **the concatenation will create a new object of string**, which will be talhamohammed

**We can delete a tuple object but we cannot delete anything inside a tuple.**
so,
t1 = (1, 2, 3, 4)
del t1, this will delete the t1
del t1[-1] this will not be possible, because tuples are immutable.

### Operations on Tuples:
1. Concatenation:
We can concatenate 2 tuples, it will be a new object with the values of t1 and t2, but t1 and t2 will remain the same.
So, t1 = (1, 2, 3), t2 = (4, 5, 6)
t3 = t1+t2 
print(t3) → (1, 2, 3, 4, 5, 6)

2. Multiplication:
t1 = (1, 2, 3)
t3 = t1 * 3, this will create a new tuple in which t1 will be repeated 3 times
print(t3) → (1, 2, 3, 1, 2, 3, 1, 2, 3)

3. Membership operator or in: same as in lists

### Functions of Tuples:
1. len() : returns len of the tuple
2. min(): returns min number in a tuple
3. max(): returns max number in a tuple
4. sum(): returns sum of all numbers in a tuple
5. sorted(): sorts a tuple in ascending order but converts it to a list

Tuples are read only data type, because tuples are immutable, write operations are not possible once a tuple is created.
Wherever data integrity is important we can use a tuple.

## Lecture - 26 
### Sets
Sets do not allow duplicates
Sets have no indexing/slicing
Sets don’t allow mutable data types
Set itself is a mutable data type.

### Creating a Set
s1 = set()
s1 = {1, 2} **both set and dictionary or map are represented with curly braces.**

**Note:** An empty set cannot be created by doing s1 = {}, this will by default create a dictionary. If we want to create an empty set we have to create by doing s1 = set(), using the constructor set().

Sets can also have mix of different data types:
s1 = {1, True, “Hello”, 4.5}

**Sets cannot store mutable data types because set itself is a mutable:**
It cannot store a list, s1 = {[1, 2, 3]} this is not possible
It can store a tuple, or a string because these are immutable, s1 = {(1, 2, 3), “Hello”}

Also, a set automatically stores elements in sorted order:
s1 = {2, 3, 1}
print(s1) → this will print {1, 2, 3}

Similarly, s1 = {(1, 2, 3), “Hello”}
print(s1) → this will print {“Hello”, {1, 2, 3}}

This happens because the set internally uses hashing, the algorithm creates a hash for each element, and the elements are arranged according to their hash values.

Also, sets have no indexing, sets do not follow the order of elements in which they are sent into a set.

We cannot create 2D or 3D sets, because set is a mutable type and set does not store mutables.
s1 = {{1, 2}, {3, 4}} // this is not possible.

### Accessing Items in a Set:
We cannot access items in a set similarly we cannot delete items from a set, Indexing and slicing will not work.

We might think we will turn the set to a list, modify the list and turn it back to a set, this will create a new set with the modification but the original one will still remain the same.

Even though set is a mutable type we cannot make modifications by replacing one element with another from it.

### Adding and Deleting items from a Set:
We use the add() function to add an item to a set.
s1 = {1, 2, 3}
s1.add(4)

We can delete a whole set using del keyword
We can delete an item using the remove() method.

s1 = {1, 2, 3}
del s1 → this will remove s1 from the memory

s1 = {1, 2, 3}
s1.remove(3) → this will remove 3, making the set {1, 2}

We can also use pop(), this will delete the last item from the set
s1 = {1, 2, 3}
s1.pop(), this will remove 1 and not 3, because internally the set uses hashing, and the hash of 1 might be at last than hash of 3.

### Hashing:
We can search or look if an element exists in a set using the membership operator in.
Add, Searching and Removing take O(1) time in a set and a dict. Because internally the elements are hashed and stored in a bucket. If we have to check if an item exists, then python hashes that element again and checks the corresponding bucket immediately, since it has the hash it can reach the exact spot immediately giving O(1) time.

Similarly, removing is also O(1), because an element which is to be removed is hashed and looked up straight into the bucket and removed.

Similarly, adding an item is also O(1), due to hashing.

### Why does Set only store immutable and hashable data ?
Because it is easy to maintain O(1) insertion, removal and search of an item. Internally set uses a hash table (similar to an array) to store items. When an item is inserted in a set, it is hashed and at the hash value bucket the item is stored. 

Now, when the same item is searched in a set, python creates its hash and directly looks into the corresponding cell in the hash table. Similarly for delete.

If it stores mutable data like a list,
l1 = [1, 2, 3]
s1 = {l1}
Let’s say for example l1’s hash value is 6, then [1, 2, 3] will be stored at the 6th bucket.

Now, let's say someone modifies the l1
l1.add(4), now l1’s hash changes let's say it becomes 7.

Now when someone tries to check if l1 exists in the set, then he won’t be able to find it because it's hash is changed, the l1 which was stored its hash was 6 now its 7, similarly we won’t be able to remove l1 because there is nothing at 7 in the hash table.

That’s why a set allows a tuple but not a list, a tuple is immutable i.e. no items can be inserted or deleted once a tuple is created, similarly int and string.
Since these are immutable they cannot be modified if it cannot be modified its hash will always remain constant. 

### Operations on a Set
1. Concatenation will not work on a set
2. Multiplication will not work on a set
3. Membership will work, i.e. 1 in s1, for i in s1 etc

### Functions on a Set
1. len() to find the len of a set
2. min() and max()
3. sum() 
4. sorted() - this will return a copy of a set but it will be a list.
s1 = {3, 2, 1}, sorted(s1) will return a list, sorted(s1, reverse=True) will sort in ascending order and return a list.

5. union() - it returns a new set with unique elements from both the sets.
s1 = {1, 2, 3}, s2 = {2, 3, 4, 5, 6}
s1.union(s2) → {1, 2, 3, 4, 5, 6}

6. intersection() - it returns a new set with common values from 2 sets.
s1 = {1, 2, 3}, s2 = {2, 3, 4}
s1.union(s2) → {2, 3}

7. difference() - it returns a new set which will have those elements from one set which are not there in the other set.
s1 = {1, 2, 3}, s2 = {2, 3, 4}
s1.difference() → {1}
s2.difference() → {4}

8. isdisjoint() - returns true if both sets do not have any common items or else false.
s1 = {1, 2, 3}, s2 = {2, 3, 4}
s1.isdisjoint() → False, because 2 and 3 are common in both s1 and s2.

9. issubset() - returns true if all elements of s1 exist in s2 or vice versa.
s1 = {1, 2, 3}, s2 = {2, 3, 4}
s1.issubset() → False, because s2 does not have 1

10. issuperset() - returns true if s1 consists of all elements of s2 or vice versa.
s1 = {1, 2, 3}, s2 = {2, 3, 4}
s1.issuperset() → False, because s1 does not have 4

## Lecture - 27
### Dictionary 
Dictionary stores data in the form of a key, value pair.

- Dictionary is mutable.
- Dictionary has no indexing.
- Dictionary key must be of immutable type and value can be of mutable type.
- Keys should be unique.

### Creating a Dictionary
d1={}
d = {1: “talha”, 2:“yaseen”}
d = {1: “talha”, 1:”yaseen”}, this will not throw an error, instead it will replace “talha” with “yaseen”. The most recent will be replaced by the latest one.

We can create a dictionary inside a dictionary, basically it is same as a JSON object
ex:
```{
	id: 1,
	name: “BTC”,
	data: {
		“price”: 67000,
		“vol”: “10M”
}
}
```
### Accessing items of Dictionary:
```d = {
	“id”: 1,
	“name”: “BTC”,
	“data”: {
		“price”: 67000,
		“vol”: “10M”
    }
}
```

d[“id”] → this will give 1
d[“data”][“price”] → this will give 67000

We can also use the get() function to get a value of a key.
ex: d.get(“name”)

### Editing a Dictionary:
```
d = {
	“id”: 1,
	“name”: “btc”
}
```

d[“name”] = “eth”

### Adding new key value pairs into a Dictionary:
```
d = {
	“id”: 1,
	“name”: “Bitcoin”,
	“data”: {
		“price”: 67000,
		“vol”: “10M”
    }
}
```

d[“code”] = “btc”
d[“data”][“mcap”] = “340B”

### Deleting a key in Dictionary:
We can delete a whole dictionary using del d.
del d[“code”], this will delete the code key value pair.

### Membership operator:
code in d → this will return true.

for i in d:
	print(i) **this will only print the keys**

for i in d:
	print(i, d[i]) **this will print both the key and the value**

### Functions on Dictionary:
1. len() - returns the number of key value pairs present in the dict
2. min() - returns the key which is min, incase keys are of type string it will return the key which is lexicographically smallest.
3. max() - returns the key which is max
4. sorted() - sorts the dict keys in ascending order and returns the keys in a list.
5. sorted(d, reverse=True) - sorts the dict keys in descending order.

6. keys() - it returns a list of all the keys in a dict.
ex: d.keys() → [“id”, “name”, “data”]

7. values() - it returns the values of all the keys in a list.
ex: d.values() → [1, “Bitcoin”]

## Lecture - 28
Variable Referencing, Mutability, Garbage Collection
Python has a stack memory and a heap memory, 
**Stack stores:**
1. Function call frames
2. Local variables
3. Control flow
5. Return values

**Heap stores**
1. Objects 
2. Data or value of the objects

When we write code in a python file, the file will be in the ROM/hard drive. But when we run the file or at runtime, the variables in the code, the functions and all are loaded onto the RAM.

a = 5, 5 will be created as an int object in heap memory and a will be having a reference to the memory address of 5.
b = a, b will also have the same reference id of 5 as a has.
since a is a variable it will be in the stack memory with a reference to the memory address of int object 5.

del b, this will not delete 5, but it will delete the reference b was holding. 5 will still remain in the memory as it is, as a is still pointing at it.

del a, now a’s reference is also deleted, now 5 will be cleared from the memory as there are no variables referencing that address.

We can also check how many references a memory address has or a value has,
ex: a = 5
b = a
c = b
So, 5 has 3 references from a, b and c
We can check this using the getrefcount() method from the sys module. It will return an int letting us know how many references are there to a specific object.

`ref = sys.getrefcount(a)`

### Garbage Collector
When there are no variables referencing a memory address, then that address will be cleared by a garbage collector, which is also a program.

It continuously monitors the memory at regular intervals to check if there is any memory location which has no references, if yes it clears it out from the memory.

Weird Behaviour of Python Memory Management:
a = 2
b = a
c = b

sys.getrefcount(a) 
The ref count should be 
1 from a
1 from b
1 from c
1 from getrefcount // because getrefcount will also have a ref in its stack frame
So the total count should be 4, but it won’t be. Because 2 is a common number then this will be already being used in other software so 2 will be present in the memory and there will be many references from variables in other software programs, hence the count will be way greater than 4.

If a is a less common number like,
a = 717
b = a
c = b
Now, the getrefcount will return 4, because it is highly possible that only our program has created 717 in the memory.

**Same id / memory address for all variables storing or aliasing numbers from -5 to 256**
x = 256
y = x
z = y
print(id(x)) 
print(id(y))
print(id(z))
All the 3 print statements will print the same memory address. This is because python by default fills up numbers from -5 to 256 automatically because numbers in this range will be the most used ones, this is software optimizing for making things fast.

Once we start creating objects which are smaller than -5 and greater 256, it will start allocating new memory addresses. i.e numbers like -6, 257 etc

### How Lists are stored in Memory ?

We can see that separate objects are created in the memory for 1, 2 and 3, and the cells of the list are holding the reference or memory id of 1, 2 and 3 in them.

![Lists in memory](images/lists_in_memory.png)

### Mutability:
The ability to change or edit the data in its memory location. Mutability depends on data type, few data types can be modified in the same memory location and some do not allow this.
![Immutable and Mutable types](images/immutable_&_mutable_types.png)


### Immutable data types like tuple, int, boolean etc cannot be changed once created.
ex: x = 4 this will create a new int object in the memory, if we overwrite x = 5, then 4 will stay as it is in the memory a new object for 5 will be created and x will start pointing to the new object.

t = (1, 2, 3) a tuple once created cannot be modified we cannot insert or delete, 
t = (1, 2, 3, 4), now 4 will not be inserted in the above tuple, instead a new tuple will be created and in the memory which will have 1, 2, 3 and 4.

similarly, a = “taz”
a = “hi” + a, // this will create “hi taz” but it will be a separate string object in the memory a will shift its reference from the previous object “taz” to “hi taz”.

### Mutable data types:
l = [1, 2, 3]
l.append(4) → this will not create a new list, but add 4 to the same l, as list is a mutable type.

### Note:
If we do concatenation of lists a new list will be created
l1 = [1, 2, 3], l2 = [4]
x = l1 + l2, x will be a new list, 4 will not get added to l1, but a new list will be created.

### Cloning:
When working with mutable data types, it is always best to clone the data type or create a new copy before making changes, because changes on a mutable type can cause problems in case that particular data type has to be kept unique. In such cases it is best advised to use immutable types, but still in case we have to make any changes to a mutable type we will do it by cloning or making a copy of the existing type and we will make changes on the copy.

ex: l1 = [1, 2, 3]
l2 = l1[:] **this will create a clone of l1 in a new location in the memory.**
l2.append(4) **this will not alter l1 now.**

t1 = (1, 2, [3, 4])
t1[-1][0] = 100 
**this is possible, even though tuple is immutable, but change being made is on a list inside the tuple, the tuple stores references of 1, 2 and the list.** 

t1 = ([100, 2], [3, 4])
c[0] = [200, 3] 
**this will not work because we are asking the tuple to change its reference to a new list.**

## Lecture - 29
### Functions:
Functions are a block of code that are used to execute a specific task. Functions help us make software modular and easier to understand.


### Syntax of a function:
```
def func_name(param):
	“”” Doc String ”””
	//body of the function
	return value
```

def - define keyword, used to define a function
identifier - function name is an identifier, we cannot start identifiers with numbers and we cannot use any special characters except the underscore.
Doc string - doc strings are used to write comments on what a function does, what kind of parameters it takes and what does it return, it is basically written to provide understanding of the function.
return value - it is the value which a function returns.

### How does a function execute in memory ?
When a module or a .py file is executed a global frame is created for that module inside the call stack. This frame will have all the global variables, function definitions and classes. 
Each module gets its own global frame.
The global frame lasts until the module finishes execution.

main.py
```
def getSum(a, b):
	return a + b

x = getSum(2, 3)
```

### Now when python main.py is run on the terminal

![Immutable and Mutable types](images/call_stack.png)

- Python loads the main.py module
- A global frame is created in the call stack, with the object getSum, x variable
- After loading, the interpreter reaches the getSum() function 
- A new frame for getSum is created on the call stack with the arguments a and b and their values 2 and 3
- The function executes and returns a+b 
- Once the function returns its frame is destroyed and x gets the value of a+b
- When a function has no return value still it returns None.

### Arguments vs Params:
```
def sum(a, b):
	return a + b
```

Here a and b are parameters
sum(2, 3), 2 and 3 are arguments, the values passed to params are called arguments.

### In python we have 4 types of Arguments:
- Default Arguments
- Positional Arguments
- Keyword Arguments
- Arbitrary Arguments

1. Default Arguments
When defining a function we can set default values to the params of a function, ex:
```
def power(a=1, b=1):
	return a**b
```

How does this help ?
Let's say someone just called the function with no arguments or a single argument
sum() // this won’t throw any error
sum(2) // this also won’t throw any error

If there are no default arguments, then the interpreter will throw an error and the code will break.

2. Positional Arguments
When sending arguments to power(2, 3), 2 will be sent to a and 3 will be sent to b, hence these numbers go to the arguments of the actual position.

3. Keyword Arguments
What happens if we do power(b=2, a=3) ?
The ans will be 9, because since we already set a = 1 and b = 1 as default arguments, now a and b will be pointing towards the object 1 in the memory.

Now, if we do power(b=2, a=3), now we shift the pointer of a to object 3 and b’s pointer to object 2.
Hence inside the function we return a**b, a is 3 and b is 2, so 3**2 = 9
Even though if we take according to the position we are sending 2 at a and 3 at b, but we explicitly mention that b=2 and a=3

This is called Keyword argument, it is prioritized over positional arguments. These can be used when we have a function which has a lot of params but we don’t remember the positions of each param, we only remember names, then we can use this method.

4. Arbitrary Arguments
Print function can take in multiple arguments separated by commas and it will print all of those. This is possible due to Arbitrary Arguments.

```
def sum(*numbers):
	sum=0
	for i in numbers:
		sum+=i
	return sum
```

When python sees * asterisks before a param, it gets the message that this method will accept multiple arguments, hence it will internally create a tuple and store all the arguments inside that tuple. Hence, this argument becomes an iterable.

We can now send arguments separated by commas to sum

x=sum(1, 2, 3, 4) // sum will return 10

### Global variable vs Local variable
```
x = 5

def sum(x):
	y = 1
	print(y+x)

sum(x)
print(x)
```

The module will be loaded in the memory and a frame will be created with global variable x = 5 and function sum in it.

When sum is called a separate frame is created in the stack, this will have the argument x = 5, and the local variable y = 1, it will print 6 

After printing, the sum frame will be destroyed and finally the last line will print 5.
The global x=5 was not altered because integers are immutable types, when x was passed to sum it created its own local variable x from the argument 5 in its frame, hence the global x was unaltered.

```
def g(y):
	print(x)
	print(x+1)
x=5
g(x)
print(x)
```

g(5) frame will have create a local variable y=5
It will print(x), but it does not have x, in this case the g function will access the global x and print 5
Then it will also print x+1 or 6 by creating a new int object 6, since integer is immutable, the global value x=5 won’t change, a new object x+1 = 6 will be created.

Finally the frame will be removed and in the global frame since there is print(x), x was unaltered hence 5 will be printed.

```
def h(y):
	x+=1
x=5
h(x)
print(x)
```

The above code will throw an error, because the function h is trying to modify a global variable, but we might be thinking since x is immutable why not create another object 6 and point x to it, but this is not possible, since it is a global variable other functions might also be using x, hence python does not allow changing of global variables.

So we learnt,
Global variables - variables in the global scope that can be accessed by any function, class or a variable and anywhere in a module.
Local variable - variables in the local scope only accessible inside a function, gets destroyed when the function is done executing.
***A function can use a global variable but it cannot alter the global variable.***

```
def h(y):
	global x
	x+=1
	print(x)

x=5
h(x)
print(x)
```

***Even though it is a bad practice, python has still provided a way to change the global variable by using the global keyword.***

### Nested Functions
```
def f():
	print(“inside f”)
	def g():
		print(“inside g”)
		f()
	g()
```

f() // This will take us in an infinite loop
f() → g() → f() → g() →  f() → g(), the interpreter will end this loop as there is a set limit on how many function calls can exist inside a call stack.

Also the inner function g() can’t be called from the global scope.

### Note:
Everything in Python is objects
Functions are also objects, to prove this
def f(num):
	return num**2

x=f
x(2) → this will print 4, because since everything in python is an object x can point to a function f which is an object, hence now x is also a function.

We can also del a function i.e. we can remove references to it and the GC will eventually remove it when there are no references.

```
def num(x):
	print(x)

x = num

del num
x(5) 
```

this will print 5, because x is pointing to the function object num
There were 2 pointers pointing towards num object, num and x, num got deleted and x is still pointing towards num and keeping it alive in the memory. 
Since num is the name of the function it is also the identifier hence it points to the function object taking in x.

### Since function is also an object we can also store it in a list, tuple etc
```
def g(y):
    return y**2

t = (1, 2, 3, g(2))

print(t) → (1, 2, 3, 4)
```

So we can,
1. Rename a function
2. Delete a function
3. Storing a function
4. Returning a function
5. Function as an argument

### Function as an argument
```
def func_a():
	print(“inside func_a”)

def func_c(z):
	print(“inside func_c”)
	return z()

print(func_c(func_a))
```

Since func_c is called “inside func_c” will be printed, 
func_c after printing will return but first will call z(), z is func_a, so “inside func_a” will be printed.

```
def f():
	def x(a, b):
		return a + b
	return x

val = f()(2, 3)
print(val)
```

f() is called
f will return x which is a function
now to that return function we pass 2 and 3 and also call it
this function will return a+b = 5

We can also write this as,
val = f()
x = val(2, 3)
print(x)

Since, f returns a function object, val will store that, now we can pass 2 and 3 to value.

### Benefits of using a function:
1. Code mularity
2. Write once use forever
3. Improves Code readability





