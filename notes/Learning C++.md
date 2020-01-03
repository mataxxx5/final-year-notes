---
attachments: [Clipboard_2020-01-02-19-27-49.png]
tags: [FYP-Research]
title: Learning C++
created: '2020-01-02T17:33:43.008Z'
modified: '2020-01-03T13:48:48.207Z'
---

# Learning C++

## Features
- Procedural(can be imperative and object orientated)
- Statically typed
- Case-sensitive

## Demo Program
```
using namespace std;

// main() is where program execution begins.
int main() {
   cout << "Hello World"; // prints Hello World
   return 0;
}
```
- statement termination with ```;```
- code block declared with ```{...}```
- return type is defined in function defintion ```returned_type function_name```
- comments defined with ```//``` and ```/**/```

## Language Conventions
### Variables
#### Variable definition
- variables are defined by specifiying data type and variable name(identifier) ```int cost;```
- several variables of the same type can be defined, seperated by commas ```int num_one, num_two, num_three;```
- keywords(reserved words) can't be used as variable names
- uninitialised variable in general will hold the value of undefined

#### Variable Declaration
A variable can be declared, which will speed up compilation time of the code as it is assumed that no more detail is needed for the variable, and it can move on to compiling the rest of the code. The declaration is only used during compilation and the actual definition is used when linking the program(excution time). Variables can be declared several times but can only be defined once per file. 

Declaring global variables is the same as declaring local vairbales  ``` int c;```

#### Lvalues and Rvalues
L values refer to memory location and R value refers to data stored at that memory location, the l and r refers to their position in variable assigment

#### Constants/Literals
Constants are variables immutable variables that can be chnaged after they're values have been defined, they can hold values of any primitive C++ datatype:
- Numerals, 
- Floating-Point Numerals
- Characters 
- Strings
- Boolean Values.
A constant can be defined by either a #defined preprocessor ```#define data_type variable_name```
Or by const keyword ``` const data_type variable_name```

### Functions
### Function Declaration and definition
```
return_type function_name( parameter list ) {
   body of the function / function definition
}
```
the declaration of the function must specify return_type (if function returns something) the name, by which compiler idetifies the function and parameters/argumnets that the function takes in.

<strong> By default, paramenters are treated as pass by value, therefore modifying the value of parameter inside a function will not affect the variable's name outside the scope of the function</strong>

Additionally C++ allows for optional arguments

### Data Structures
#### Arrays
Arrays are fixed-size sequential collections of elements that are the same in type
##### Declaration
initialising array:
```type array_name[array_size];```
to initialise an array with values:
```type array_name[3] = {element0, element1, element2};```
##### Accessing
> <font color='red'> Array indexing works as [0..array_size-1]</font>

Array elements can be accessed by index and retreived as:
```type variable_name = array_name[index];```
Array elements can be assigned also using the index :
```array_name[index] = value;```
##### Tips
- You can pass a pointer of an array to function by specifying array name without index
- You can gener
### Scope
#### Local Variables
Variables defined in a function or a code block, and can only be accesed in their code block. the local variable of the same name is used over global by the language. Local variable must be initialised

#### Global Variables
Defined outside of all functions and persist throughout the lifetime of the program, it is immutable by function definitions(local variable of the same name is seperate variable). Global variable is initiliased by the language to certain value according to it's data type
![](@attachment/Clipboard_2020-01-02-19-27-49.png)

### Storage Classes
They are specifiers that precede the type of variable in defintion and determine scope and lifetime of variables/functions

#### auto
Default storage class for all the local variables(is implicitly defined when definign any local variable; hence auto)

#### register
This class defines which variables should be stored in stored in register of the CPU rather than RAM(for quick access) and has a size limited to one word (2 bytes)  and has no memory location. The storage in register is not garuanteed

#### static
##### use with local variables
It persist the local variable throuhout the lifetime on the program and is reused between function calls rather than created/destroyed each call

##### use with global variables
It restricts the scope of the global variable to the file it's defined in

##### use with member data of a class
It makes the instances of the class share one copy of the variable

### Looping
Same looping as java with the exemption of a for each loop and addition of do while loop
#### Loop control
control statements that change how looping 
break - to break out of loop
continue - skips loop body till next iteration
goto - transfers control to a labelled statement
### Decision making
the usual if statments and swtich statements exists as well as ternary if

## Best Practises
### Naming Conventions
- types start with upper case: ```MyClass```
- functions and variables start with lower case: ```myMethod```
- constants are all upper case: const double ```PI=3.14159265358979323;```
- all other names use snake case: ```unordered_map```.
- ```m_``` stands for "member" data and is used to distinguish from public data
- name function parameters with an ```t_``` prefix
- <font color='red'> Don't name anything starting with </font> ```_``` 

## Learning to complile/build, run and debug C++ code in VScode
> [VSCode Guide](https://code.visualstudio.com/docs/cpp/config-mingw)

<strong>To compile/build : </strong> configure compiler path for the project and create a build task json
<strong> To debug : </strong> confogure debug settings which should generate launch, then paste boilerplate debug settings from the resource mentioned above
<strong> To run : </strong> the built code, depends on the build settings, but if it's an .exe then run by `./exe_name.exe`

## Useful Resources
[best practices guide](https://github.com/lefticus/cppbestpractices)
