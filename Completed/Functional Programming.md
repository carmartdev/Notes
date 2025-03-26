<span class="tag">Tags</span>:   [[Coding]]

Created at 2024-10-23 17:10
<span class="tag">Status</span>: <span class="danger">Not done yet</span>
<span class="danger">Sources</span>: Missing CS Courses

# Functional Programming
## Imperative vs. Declarative languages

### Declarative languages
You don't say how to solve a problem but you **declare** what the problem is.
#### Logic programming
In here we talk about functional programming
#### Functional programming
You should only describe ==what== the problem is and not ==how== to solve it.
### Example: length algorithm
#### Java: Imperative
```java
class Element{
	Data    value;
	Element next;
}
class List{
	Element head;
	static int length (list l){
		int n = 0;
		while(l.head != null){
			l.head = l.head.next;
			n = n + 1;
		}
		return n;
	} 
}
```

![[pixil-frame-0(1).png]]
- Programs can have side-effects(`l = erased`).
- Programmer has to consider what will happen in the memory of the computer and the machine-oriented features.
- Statements are executed **from top to bottom** and we have control structures(like while loops and etc.)
#### Haskell: Declarative (Functional)
We have to define what language length is.
 - (A) If the list `l`is empty, then `len(l)=0`.
 - (B) If list `l` is not empty and if `xs` is the list `l` without the first element, then `len(l) = 1 + len(xs)`.
##### Syntax of Haskell:
In Haskell:
```haskell
x : xs -- list which results from list xs by inserting x in front
```
is a list where the list starts with `x` and and `xs` is the remainder of the list(the rest of the list without the first element)

###### Example of lists:
```haskell
15 : [70, 36] -- [15, 70, 36]
15 : 70 : 36 : [] -- [15, 70, 36]
```
- So `:` means list insertion in front.
- `:` associates to the right.
==> **_Every non empty list can be written as `x = xs`._**
##### The Haskell Program:
```haskell
len :: [                Int               ] -> Int
--     [Type of list with integer elements]
len [] = 0 -- you can write it like len([]) = 0
len (x:xs) = 1 + len xs
```
###### Execution:
```haskell
len [15, 70, 36]
```
###### How it works?
```haskell
len [15, 70, 36]
= 15 : [70, 36] -- x : xs
= 1 + len [70, 36]
= 1 + 1 + len [36]
= 1 + 1 + 1 + len []
= 1 + 1 + 1 + 0
= 3
```

#### Characteristics of Haskell
- no loops
- no side-effects, application of a function to the same arguments always yields the same results (this is called referential transparency).
- Polymorphic type system (generic types):
```haskell
-- the idea of polymorphic type system 
len :: [d] -> Int -- d would be some arbitrary data type (you can call it anything)
```
- Memory management is done automatically (has a garbage collector).
- Functions are first-class data-objects (functions can take functions as arguments or results)
- Lazy Evaluation (only those parts of the code are evaluated that are really needed for the result) ->*Only in Haskell not in Lisp, ML, Scheme and etc.*

## Chapter 1: Introduction to Haskell
### Installing Haskell
You should visit https://www.haskell.org/ and download GHCi (Glasgow Haskell Compiler Interactive mode (interpreted))
### 1.1 Syntax and Constructs of Haskell
Declarations, Expressions, Patterns and Types
#### 1.1.1 Declarations
Haskell program is a sequence of declarations (starting at the same position (start of the line)). Declarations describe a function.
##### Introducing syntax of Haskell by grammar (non terminals are italic here)
There is to kinds of declarations:
type declarations and function declarations
###### Comments:
```haskell
-- this is a comment
```
##### Type Declarations
```haskell
square :: Int -> Int -- gets int and gives int
square, double :: Int -> Int -- [domain type] -> [range type]
```
##### Types:
Int, Bool, Double, Char, ...
```Haskell
Int -> Int -- types of functions from int to int
[Int] -- type of lists with integer elements
[Int] -> Int -- function that takes a list of integers and gives an integer (like a maximum function or a sum function)
[[Int]] -- list of lists of integers
[Int -> Int] -- list of functions going from int to int
```
Type declarations don't have to be written by the programmer but Haskell infers them automatically. The good way of doing it is to write type declarations in your program.

##### Variable Names
Variable names are strings starting with a lower-case symbol.

##### Function Declarations
```haskell 
  square x                   = x * x
--[function left hand side]  [function right hand side]
```
**The left hand side**: `var pat` has a variable that is the name of the function and a pattern that describes the expected arbitrary argument.

**Pattern:** *Special expression describing the expected arguments.*

**The right hand side:** `= expression`

Basic operations in Haskell are predefined (like `&&`, `||`, `not`, `>=`, `>`, `=`, `==`, `+`, `-`, `*`, `/` and etc.)
#### Execution of Functional Program
```haskell
square :: Int -> Int
square x = x * x
```
##### Evaluation by **Term Rewriting**
###### Term Rewriting:
- (1) Find a sub-expression such that a left hand side matches(instantiate variables in the defining equation) the sub-expressions.
- (2) **Replace** the **sub-expression** by the corresponding instantiated **right hand side**.

```haskell
square (12 - 1)
```
**Evaluating `-`**:
```haskell
square 11
--then
= 11 * 11
-- then
= 121
```

	End Of SESSION 1
### 1.2 Functional Programming Technics

# References