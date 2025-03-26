
<span class="tag">Tags</span>:   [[Coding]] [[Programming in C]] 

Created at 2024-09-30 22:09
<span class="tag">Status</span>: <span class="danger">Not done yet</span>
<span class="danger">Sources</span>: Ziglings

# Zig

## Hello Zig?

### An Introduction to functions

Zig functions are private by default but the main() function should be public.

 A function is made public with the "pub" statement like so:
```c
pub fn foo() void {
	...
}
```

### The Actual "Hello World"
```c
const std = @import("std");

pub fn main() void {
    std.debug.print("Hello world!\n", .{});
}
```

## Introduction to STD

### Importing the STD library
The `@import()` function is built into Zig. It returns a value which represents the imported code. It's a good idea to store the import as a constant value with the same name as the import:
```c
const foo = @import("foo");
```
### Real example
```c
const std = @import("std");

pub fn main() void {
    std.debug.print("Standard Library.\n", .{});
}
```

For the curious: Imports must be declared as constants because they can only be used at compile time rather than run time. Zig evaluates constant values at compile time. Don't worry, we'll cover imports in detail later.
Also see this answer: https://stackoverflow.com/a/62567550/695615

## Assignment

### Constants and Variables
`const` values cannot change.
`u`     types are "unsigned" and cannot store negative values.
`8`     means the type is 8 bits in size.

Example: 
foo cannot change (it is **CONST**ant)
bar can change (it is **VAR**iable):
```c
const foo: u8 = 20;
var bar: u8 = 20;
```

### Signed and Unsigned Integers

Example: 
foo cannot be negative and can hold 0 to 255
bar **CAN** be negative and can hold -128 to 127
```c
const foo: u8 = 20;
const bar: i8 = -20;
```

### 8Bits vs 16Bits

Example: foo can hold 8 bits (0 to 255)
bar can hold 16 bits (0 to 65,535)
```c
const foo: u8 = 20;
const bar: u16 = 2000;
```

## Print function
Perhaps you noticed before that the print function takes two parameters. Now it will make more sense: the first parameter is a string. The string may contain placeholders `{}`, and the second parameter is an "anonymous list literal" (don't worry about this for now!) with the values to be printed.

```c
std.debug.print("{} {} {}\n", .{ n, pi, negative_eleven });
```
## Arrays
Let's learn some array basics. Arrays are declared with:
```c
var foo: [3]u32 = [3]u32{ 42, 108, 5423 };
```

When Zig can infer the size of the array, you can use `_` for the size. You can also let Zig infer the type of the value so the declaration is much less verbose.
```c
var foo = [_]u32{ 42, 108, 5423 };
```

Get values of an array using array \[index] notation:
```c
const bar = foo[2]; // 5423
```

Set values of an array using array \[index] notation:
```c
foo[2] = 16;
```

Get the length of an array using the len property:
```c
const length = foo.len;
```
We can use **\*\*** to multiply the array like this:
```c
const d = [_]u8 {1, 2, 3}**2; // = 123123
```
We will learn later that **\*\*** and **++** will operate at the compile(comptime).
## Introduction to strings
In Zig strings are stored as an array of bytes:
It means that these two statements:
```c
const foo = "Hello";
```
and
```c
const foo = [_]u8{'H','e', 'l', 'l', 'o'};
```
are equivalent with each other.
Now we know that strings in Zig are a bit complicated **:/**

Here's a fun one: Zig has multi-line strings!  To make a multi-line string, put '\\\\' at the beginning of each line just like a code comment but with backslashes instead:
```c
const two_lines =
    \\Line One
	\\Line Two
;
```

See if you can make this program print some song lyrics:
```c
const std = @import("std");
 
pub fn main() void {
    const lyrics =
        \\Ziggy played guitar
        \\Jamming good with Andrew Kelley
        \\And the Spiders from Mars
    ;
```

`008 _quiz.zig.zig`

## If Statements

Now we get into the fun stuff, starting with the 'if' statement!
```c
if (true) {
    ...
} else {
    ...
}
```
Zig has the "usual" comparison operators such as:
`a == b`   means "a equals b"
`a < b`    means "a is less than b"
`a > b`    means "a is greater than b"
`a != b`   means "a does not equal b"

The important thing about Zig's `if` is that it **only** accepts boolean values. It won't coerce numbers or other types of data to true and false.
```c
const std = @import("std");

pub fn main() void {
    const foo = 1;

    // Please fix this condition:
    if (foo == 1) {
        // We want our program to print this message!
        std.debug.print("Foo is 1!\n", .{});
    } else {
        std.debug.print("Foo is not 1!\n", .{});
    }
}
```

If statements are also valid expressions:
```c
const foo: u8 = if (a) 2 else 3;
```
```c
const std = @import("std");
 
pub fn main() void {
    const discount = true;
 
    // Please use an if...else expression to set "price".
    // If discount is true, the price should be $17, otherwise $20:
    const price: u8 = if (discount) 17 else 20;
 
    std.debug.print("With the discount, the price is ${}.\n", .{price});
}
```

## While
Zig 'while' statements create a loop that runs while the condition is true. This runs once (at most):
```c
while (condition) {
	condition = false;
}
```
Remember that the condition must be a boolean value and that we can get a boolean value from conditional operators such as:
`a == b`   means "a equals b"
`a < b`    means "a is less than b"
`a > b`    means "a is greater than b"
`a != b`   means "a does not equal b"

```c
const std = @import("std");

pub fn main() void {
    var n: u32 = 2;

    // Please use a condition that is true UNTIL "n" reaches 1024:
    while (n<1024) {
        // Print the current number
        std.debug.print("{} ", .{n});

        // Set n to n multiplied by 2
        n *= 2;
    }

    // Once the above is correct, this will print "n=1024"
    std.debug.print("n={}\n", .{n});
}
```

Zig `while` statements can have an optional `continue expression` which runs every time the while loop continues (either at the end of the loop or when an explicit `continue` is invoked - we'll try those out next):
```c
while (condition) : (continue expression) {
	...
}
```
Example:
```c
var foo = 2;
while (foo < 10) : (foo += 2) {
	// Do something with even numbers less than 10...
}
```

See if you can re-write the last exercise using a continue expression:
```c
const std = @import("std");

pub fn main() void {
    var n: u32 = 2;

    // Please set the continue expression so that we get the desired
    // results in the print statement below.
    while (n < 1000) : (n+=n) {
        // Print the current number
        std.debug.print("{} ", .{n});
    }

    // As in the last exercise, we want this to result in "n=1024"
    std.debug.print("n={}\n", .{n});
}
```

The last two exercises were functionally identical. Continue expressions really show their utility when used with `continue` statements!
Example:
```c
while (condition) : (continue expression) {
	if (other condition) continue;
}
```

The `continue expression` executes every time the loop restarts whether the `continue` statement happens or not.
```c
const std = @import("std");

pub fn main() void {
    var n: u32 = 1;

    // I want to print every number between 1 and 20 that is NOT
    // divisible by 3 or 5.
    while (n <= 20) : (n += 1) {
        // The '%' symbol is the "modulo" operator and it
        // returns the remainder after division.
        if (n % 3 == 0) continue;
        if (n % 5 == 0) continue;
        std.debug.print("{} ", .{n});
    }

    std.debug.print("\n", .{});
}
```

You can force a loop to exit immediately with a `break` statement:
```c
while (condition) : (continue expression) {
	if (other condition) break;
}
```

Continue expressions do **NOT** execute when a while loop stops because of a break!
```c
const std = @import("std");

pub fn main() void {
    var n: u32 = 1;

    // Oh dear! This while loop will go forever?!
    // Please fix this so the print statement below gives the desired output.
    while (true) : (n += 1) {
        if (n == 4) break;
    }

    // Result: we want n=4
    std.debug.print("n={}\n", .{n});
}
```

## For
Behold the `for` loop! For loops let you execute code for each element of an array:
```c
for (items) |item| {
	// Do something with item
}
```

```c
const std = @import("std");

pub fn main() void {
    const story = [_]u8{ 'h', 'h', 's', 'n', 'h' };

    std.debug.print("A Dramatic Story: ", .{});

    for (story) |scene| {
        if (scene == 'h') std.debug.print(":-)  ", .{});
        if (scene == 's') std.debug.print(":-(  ", .{});
        if (scene == 'n') std.debug.print(":-|  ", .{});
    }

    std.debug.print("The End.\n", .{});
}
```

Note that `for` loops also work on things called `slices` which we'll see later.

Also note that `for` loops have recently become more flexible and powerful (two years after this exercise was written). More about that in a moment.

For loops also let you use the `index` of the iteration, a number that counts up with each iteration. To access the index of iteration, specify a second condition as well as a second capture value.
```c
for (items, 0..) |item, index| {
	// Do something with item and index
}
```

You can name `item` and `index` anything you want. `i` is a popular shortening of `index`. The item name is often the singular form of the items you're looping through.
```c
const std = @import("std");

pub fn main() void {
```

Let's store the bits of binary number 1101 in `little-endian` order (least significant byte or bit first):
```c
    const bits = [_]u8{ 1, 0, 1, 1 };
    var value: u32 = 0;
```

Now we'll convert the binary bits to a number value by adding the value of the place as a power of two for each bit. See if you can figure out the missing pieces:
```c
for (bits, 0..) |bit, i| {
```

Note that we convert the `usize i` to a `u32` with
`@intCast()`, a builtin function just like `@import()`.
We'll learn about these properly in a later exercise.
```c
        const i_u32: u32 = @intCast(i);
        const place_value = std.math.pow(u32, 2, i_u32);
        value += place_value * bit;
    }

    std.debug.print("The value of bits '1101': {}.\n", .{value});
}
```

As mentioned in the previous exercise, `for` loops have gained additional flexibility since these early exercises were written. As we'll see in later exercises, the above syntax for capturing the index is part of a more general ability. Hang in there!


## Fizz Buzz Game
You have to check if a number is divisible by 3 then you would replace it with Fizz and if it's divisible by 5 you would replace it by Buzz.
Fizz Buzz Wiki: https://en.wikipedia.org/wiki/Fizz_buzz
While loops are better for this Game.
```C
const std = @import("std");

pub fn main() void {
    var i: u8 = 1;
    const stop_at: u8 = 16;

    // What kind of loop is this? A 'for' or a 'while'?
    while (i <= stop_at) : (i += 1) {
        if (i % 3 == 0) std.debug.print("Fizz", .{});
        if (i % 5 == 0) std.debug.print("Buzz", .{});
        if (!(i % 3 == 0) and !(i % 5 == 0)) {
            std.debug.print("{}", .{i});
        }
        std.debug.print(", ", .{});
    }
    std.debug.print("\n", .{});
}
```

## Functions
Procedures in Zig are called functions(like C and other languages). The basic form of Zig functions is as follows:
```C
fn foo(input: type) returntype {
	return output;
}
```
### Example 1
```c
fn foo(n: u8) u8 {
    return n + 1;
}
```
- The foo() function above takes a number 'n' and returns a number that is larger by one.
- Note the input parameter 'n' and return types are both `u8`.
### Example 2
```c
const std = @import("std");

pub fn main() void {
    // The new function deepThought() should return the number 42. See below.
    const answer: u8 = deepThought();

    std.debug.print("Answer to the Ultimate Question: {}\n", .{answer});
}
fn deepThought() u8{
    return 42; // Number courtesy Douglas Adams
}
```
The key word pub stands for public.

### Parameters
Parameters are declared just like any other types`("name": "type")`:
```c
fn myFunction(number: u8, is_lucky: bool) {
	//Code Goes Here
}
```

#### Example
```c
const std = @import("std");

pub fn main() void {
    std.debug.print("Powers of two: {} {} {} {}\n", .{
        twoToThe(1),
        twoToThe(2),
        twoToThe(3),
        twoToThe(4),
    });
}
fn twoToThe(my_number: u8) u32 {
    return std.math.pow(u32, 2, my_number);
}
```
`std.math.pow(type, a, b)` takes a numeric type and two numbers of that type (or that can coerce to that type) and returns "a to the power of b" as that same numeric type.

### Example 3
```c
const std = @import("std");

pub fn main() void {
    const my_numbers = [_]u16{ 5, 6, 7, 8 };

    printPowersOfTwo(my_numbers);
    std.debug.print("\n", .{});
}
fn printPowersOfTwo(numbers: [4]u16) void {
    for (numbers) |n| {
        std.debug.print("{} ", .{twoToThe(n)});
    }
}
fn twoToThe(number: u16) u16 {
    var n: u16 = 0;
    var total: u16 = 1;

    while (n < number) : (n += 1) {
        total *= 2;
    }

    return total;
}
```
<span class="danger">We shouldn't pass arrays to functions</span>
# References
