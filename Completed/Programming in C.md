Tags:  [[Coding]]
Date: Aug, 17, 2024

Sources:
- /home/amir/.nb/ISLP/20240806105649.md

# Programming in C
  Notes from the "Programming in C" book written by Eyn-o-llah Ja'farnejad-
Qomi

## Chapter1: An introduction to the C language

### What is C?

  The C language was made in 1972 by Dennis M. Ritchie with the help of Ken
Thompson. Which is a developed version of the *BCPL* language that was made
by Martin Ritchards. The  *BCPL* language that influenced *B* language made
by Ken Thompson was influenced by the CPL and C is a lower-level and typish
version of that.

  - **C** is a  Mid-level language. programming languages can be devided in 
three levels: *High-level* languages, *Mid-level* languages and *Low-level*
languages. C  is readable like the *High-level* languages and it has direct
access to memory and it can work with bytes, bits and addresses.

  - C is a functional programming language and in this language you can use
loops like while, for and do while.

#### Levels of progeamming languages

+============================================================+
|Low-level languages|Mid-level languages|High-level languages|
|------------------------------------------------------------|
|Macro Assembler    |Java               |Pascal              |
|------------------------------------------------------------|
|Assembler          |Fortran            |Ada                 |
|------------------------------------------------------------|
|                   |C/C++              |Modula-2            |
|------------------------------------------------------------|
|                   |                   |Cobol               |
|------------------------------------------------------------|
|                   |                   |Basic               |
+============================================================+

#### Functionality of programming languages
+=============================================
|Non-functional languages|Functional languages|
|---------------------------------------------|
|Fortran                 |Pascal              |
|---------------------------------------------|
|Basic                   |Ada                 |
|---------------------------------------------|
|Cobol                   |C/C++               |
|---------------------------------------------|
|                        |Modula-2            |
|---------------------------------------------|
|                        |Java                |
+=============================================

#### Key words of the C language
+==============================================
|`auto`      |`double`      |`int`      |`struct`      |
|----------------------------------------------|
|`break`     |`else`        |`long`     |`switch`      |
|----------------------------------------------|
|`case`      |`enum`        |`register` |`typedef`     |
|----------------------------------------------|
|`char`      |`extern`      |`return`   |`union`       |
|----------------------------------------------|
|`const`    |`float`       |`short`    |`unsigned`    |
|----------------------------------------------|
|`continue`  |`for`         |`signed`   |`void`        |
|----------------------------------------------|
|`default`   |`goto`        |`sizeof`   |`volatile`    |
|----------------------------------------------|
|`do`        |`if`          |`static`   |`while`       |
+=============================================

  - C is powerfull and scalable

  - C has a fairly low amount of key words(around 30)

  - C has a good relationship with ASM

  - C is portable

  - C is case-sensetive

#### C keywords that some compilers have added to it

+===========================
|`asm`      |`_cs`  |`_ds`   |`_es` |
|`_ss`      |`cdecl`|`far`   |`huge`|
|`interrupt`|`near` |`pascal`|    |
+===========================

#### C writing instructuions

  - 1. Every line of code (or command) ends with a ";".
  - 2. You can write 255 characters on each line (or command).
  - 3. Each command is written in one or a couple of lines.
  - 4. Most of the Keywords should be written in lower-case.
  - 5. You can type a bunch of commands on one line. (NOT RECOMENDED)
  - 6. You can write comments between "/*" and "*/" or you can type it after "//" like:
```c
/* this
is a
comment*/
//this is a comment
```
### Types of data

#### Diffrent Types of data and their desired value

+=========================================
|Type              |Size in bits|Desired value                        |
|---------------------------------------------------------------------|
|`char`                     |8           |-127 to 127                          |
|`unsigned char`     |8           |0 to 255                             |
|`signed char`         |8           |-127 to 127                          |
|`int`                        |16 or 32    |-32767 to 32767                      | typedef int i
|`unsigned int`        |16 or 32    |0 to 65535                           | typedef unsigned int u
|`signed int`            |16 or 32    |-32767 to 32767                      | typedef signed int i
|`short int`              |16          |-32767 to 32767                      | typedef short int short
|`unsigned short int`|16          |0 to 65535                           | typedef unsigned short int `ushort`
|`signed short int`  |16          |-32767 to 32767                      | typedef signed short int short
|`long int`          |32          |-2147483647 to 2147483647            |
|`signed long int`   |32          |-2147483647 to 2147483647            |
|`unsigned int`      |32          |0 to 4294967295                      |
|`float`             |32          |7 decimal digits 10^-38 to 10^38     | 
|`double`            |64          |15 decimal digits 10^-308 to 10^308  |
|`long double`       |80          |19 decimal digits 10^-4932 to 10^4932|
+==================================================

### Variables

  Variables are some namespaces that are used to save data and calling  the
data by calling the variable name. You can name variables with the **z** to
**a**, **Z** to **A** and  numbers and **_**. Your varibales name can be as
long as you want   but  only  the first 31 charachters are used for calling
it. Variable names  can't   start  with  numbers they can't  have operation
marks in their names(like !@#$%^&).

#### Defining variables
```c
[Data type] [Variable name];
```
##### Examples:
```c
  int x,y;
  float m,n;
  char ch1, ch2;
  double d1;
  long int p1;
```

#### Giving value to variables
```c
[Data type] [Variable name] = [Value];
```
##### Examples:
```c
  int x, y, m = 5;
  float f1, f2;
  char ch1 = 'a', ch2 = 'A';
  f1 = 20.15
  f2 = 13.4
  m = 0
```
#### Giving input values to variables:

```c
  int x, y;
  scanf("%d%d", &x, &y);
```

### Defining constants
```c
  #define [CONSTANT NAME] [value]
```
#### Examples:
```c
  #define M 100
  #define PI 3.14
```

#### Another way of doing it:

```c
  const [Data type] [Name] = [Value];
```

##### Examples:

```c
  const int n = 100, int count = 50;
  const signed char x = 'a';
```

### Operators
*I know these so I'm just gonna' draw the tables*

+==============================+
|Operator |Name     |Example   |
|------------------------------|
|    -    |Minus    |-x or x-y |
|------------------------------|
|    +    |Plus     |  x + y   |
|------------------------------|
|    *    |Multiply |  x * y   |
|------------------------------|
|    /    |Devide   |  x / y   |
|------------------------------|
|    %    |Remaining|  x % y   |
|------------------------------|
|    --   |Decrement|--x or x--|
|------------------------------|
|    ++   |Increment|++x or x++|
+==============================+

#### Operators order
+=================================+
|    ++  --    |Highest Precedence|
|---------------------------------|
| - (Minus one)|                  |
|---------------------------------|
|    * / %     |                  |
|---------------------------------|
|     +  -     |Lowest Precedence |
+=================================+

#### Relation operators
+==================================+
|Operator|Name            |Example |
|----------------------------------|
|    >   |Greater than    | x > y  |
|----------------------------------|
|   >=   |Greater or equal| x >= y |
|----------------------------------|
|    <   |Lower than      | x < y  |
|----------------------------------|
|   <=   |Lower or equal  | x <= y |
|----------------------------------|
|   ==   |Equal           | x == y |
|----------------------------------|
|   !=   |Not equal       | x != y |
+==================================+

#### Logical operators (with precedence)
+=============================+
|Operator|Name|Example        |
|-----------------------------|
|    !   |Not |       !x      |
|-----------------------------|
|   &&   |And | x > y && m < p|
|-----------------------------|
|   ||   |Or  | x > y || m < p|
+=============================+


## Syntax (summary)
### Include
```c
#include <stdio.h> // Standard library
#include <string.h> // String manipulation
#include "lib.c" // File "lib.c" in our main directory
```

### Functions
```c
int mul(int a, int b){
//Start of code block
  int result = a * b;
  return result;
  puts("This will not be executed."); // This line will be not executed because it came after return
//End of block
}
```
#### Fibonacci
```c
int fib(int n){
  if (n <= 1){
  return n;
  }
  return fib(n - 1) + fib(n - 2); // We can do operations in the return statement 
}
```

#### Print
```c
void printing(){
  puts("Wellcome!"); // puts is like print but it can't interpolate
  printf("3 * 4 = %d \n", fib(10));
}
```
##### Specifiers
`%d` ---> signed integer **decimals** (like 99 and -42)
`%f` ---> decimal **floating** points (like 3.14, -0.01 and ...)
`%s` ---> **strings** (like "Hello" and ...)
`%%` ---> it's for writing **%**
`%p` ---> address pointers (if you give it "hello", it will return `0x7ffeefbff718`)

### Loops
```c
int c = 100;
while(c > 0){ // this loop counts from 1000 backwards 7 by 7
  printf("%d\n", c);
  c = c - 7;
}// while will run until it's condition become false
```
```c
for(int i = 0/* defining variable */; i < 100/* condition */; i += 7/* operation */){
  printf("%d \n", i);
}
```

### Conditions
```c
if(conditon){
  // Code goes here
}else if(conditon){
  // Code goes here
}else{
  // Code goes here
}
```