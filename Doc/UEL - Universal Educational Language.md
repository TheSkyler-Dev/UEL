## What is `UEL`?
`UEL` (pronounced "yuel") is a scripting language designed for easy-to-understand coding for education and teaching basic programming principles. It has COBOL's English-like syntax, but is less verbose without losing clarity.

## Getting Started
Since `UEL` is still in its design stage, there are no ways to getting started yet. This section will be updated once a toolchain is available for `UEL`.

## How `UEL` Works
In this section, the basic usage of `UEL` is demonstrated.
### Data Types
`UEL` uses type inference by default, making type declaration optional. `UEL` has three types:
- `string`
- `boolean`
- `number`
The type `number` covers the sub types `integer`, `float` and `double`, simplifying data types.

### Hello, World! - Basic I/O
`UEL` can either output information to the terminal or to a file, as well as read user input using `read-line()` from the command line or from a file. By default, `UEL` can read and write to and from text files, JSON files, CSV files and Plain text files.

as is common when learning any Programming language, let's write our very first program: the famous "Hello, World!" program, using the standard output function `print()` :

```UEL
program Hello
    print("Hello, World!")
end program
```

### Variables
Variables in `UEL` don't have to be explicitly declared with a type, however you do have to initialize them with a value as they're declared.
An example of how variables are declared in `UEL`:

```UEL
variable x equals 10
or
variable y equals 32 is type number
```

Constants are declared as follows:

```UEL
constant x equals 10
```

Variables are nullable in `UEL`, but require null values to be assigned to them. constants, on the other hand aren't nullable. there are three null values in `UEL`:
- `none`: Universal null value
- `nil`: null value of type `number`
- `empty`: null value of type `string`

### Basic Arithmetic
`UEL` uses function-based arithmetic operators. Instead of `+`, `-`, `*` and `/`, functions like `add()`, `subtract()`, `multiply()` and `divide()` are used. There are also more advanced arithmetic operators, which we will cover later.

Example: a basic number multiplier

```UEL
program math
    variable x equals 16
    variable y equals nil
    y equals read-line("Enter a Number: ")
    variable result equals multiply(x, y)
    print(result)
end program
```

### Comments
`UEL` supports both single- and multi-line comments using the following Syntax:
- `~!`: Single-line comment
- `~?`: Multi-line comment

### Control Flow
`UEL` supports both the `if/else` statement and the `case` statement, but use different syntax. While the `if/else` statement evaluates every condition sequentially, the `case` statement, evaluates a variable and jumps straight to the block of code that corresponds to the value returned by the evaluated variable.

Examples:

```UEL
variable k equals nil
k equals read-line("Enter a number: ")
if (k is less-than 0) do:
    print("Negative number")
otherwise if (k is equal-to 0) do:
    print("Number is Zero")
otherwise do:
    print("Positive number")
```

or

```UEL
varuable k equals nil
k equals read-line("Enter a menu option: ")
evaluate k:
    case 0:
        ~!Case 0 code here
    
    case 1:
        ~!Case 1 code here
    
    default-to:
        ~!default case code here
        print("Error")
```

### Data Structures

Data structures in `UEL` include arrays, dictionaries and object collections. Object collections allow you to store sets of key-value data as individual objects in a list, in a similar fashion to JSON files. Here are a few examples of how these look in `UEL`:

Arrays:

```UEL
array myArray equals [a, b, c]
```

Dictionaries:

```UEL
dictionary myDict equals {1:a, 2:b, 3:c}
```

Object collections:

```UEL
collection myCollection:
    object 0:
        "Name": "John Doe",
        "Age": 26,
        "Occupation": "Software Engineer"
    
    object 1:
        "Name": "Jane Doe",
        "Age": 30,
        "Occupation": "Police Officer"
end collection
```

Note that Dictionaries and Arrays are the only constructs in `UEL` that use curly braces and square brackets respectively.
### Loops
`UEL` supports the usual `while` and `do-while` and `for` loops. These loops run until a certain condition is met. A `while` loop will only run if its condition is met, while a `do-while` loop always executes at least once before the condition is evaluated.

`while` loop:

```UEL
variable myVar equals 0
while (myVar is equal-to 0) do:
    ~!some code
end while-loop
```

`do-while` loop:

```UEL
variable myVar equals 0
do:
    ~!some code
    increment myVar
while (myVar is equal-to 0)
```

`for` loop:

```UEL
for (variable i equals 0; i is less-than 10; increment i) do:
    ~!some code
end for-loop
```

### Ranges
`UEL` supports ranges, which are established with:

```UEL
for i in range 1 to 10 do:
    ~!some code
end for-loop
```

### Functions and Classes
#### Functions
In `UEL`, functions are quite straightforward. They let you break code, that would otherwise be within a lengthy program and would have to be written from scratch over and over again, into smaller chunks that can be called as many times as you want throughout the code. Here's an example:

```UEL
function myFunc ():
    ~!some code
end function
```

#### Classes
Classes in `UEL` are used in Object Oriented Programming (OOP) and result in more efficient source code and greater reusability, especially when the classes are in separate files, though single-file OOP is also possible. To access external classes, `call external class {class name}` is used. These contain so-called "methods", which are functions within a class. Here are some examples:

```UEL
class MyClass:
    constructor:
        ~!constructor
	
	public:
	    ~!public methods
	
	protected:
	    ~!protected methods
	
	private:
	    ~!private methods
end class
```

In another file:

```UEL
call external class MyClass
~!some other code
```

### More advanced math

Earlier, we discussed [basic arithmetic](#basic-arithmetic). Now it's time to take a look at more advanced math features in `UEL`. These include:
- Exponentiation: `exponent()`
- Square roots: `square-root()`
- n-th root: `nth-root()`
- Logarithms: `logarithm()`
- Factorials: `factorial()`

To better understand these, let's take a look at some examples of their usage:

```UEL
program more-math
    variable x equals 16
    variable y equals 2
    variable result equals nil
    
    result equals exponent(y, 2)
    print(result) ~!Output: 4
    
    result equals square-root(x)
    print(result) ~!Output: 4
    
    result equals nth-root(x, y)
    print(result) ~!Output: 4
    
    result equals logarithm(x)
    print(result) ~!Output: 4
    
    result equals factorial(y)
    print(result) ~!Output: 2
```