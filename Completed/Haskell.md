
<span class="tag">Tags</span>:   [[Functional Programming]] [[Coding]] 

Created at 2024-09-28 18:09
<span class="tag">Status</span>: <span class="danger">Not done yet</span>
<span class="danger">Sources</span>: Pister Labs YouTube channel

# Haskell

## Definitions and Bindings

Haskell uses the *=* sign to declare symbol **bindings**:
```haskell
x = 2
```

**Variables in Haskell are not Mutable**.
*Their like JavaScript **Consts** but on steroids*.

So how can we have two values for `x` in one app? we can just switch our scope; `let` lets you have local bindings:
```haskell
example = 
  let x = 44 -- this *shadows* above x
  z = x - 2
  in z * 2
-- example0 is 84
```

Variables are order-independent in Haskell:
```haskell
a = 
  if y
    then 'a'
    else 'b'  -- we can use the y variable below
y = True
```

## Essence of programming in Haskell
### Programming in Haskell is all about expressions
### Expressions evaluate to values
So what is the difference between expressions and values?
==It's the transformation it is the fact that we have to evaluate the expression to get the value.==
### Programming in Haskell: Substituting equals by equals
* Lambda Calculus for the win!
```Haskell
example = let x = 44
			  z = x - 2
		  in z * 2
```
--->
```haskell
example = let z = 44 - 2
		  in z * 2
```
--->
```haskell
example = (44 - 2) * 2
```
--->
```haskell
example = 42 * 2
```
--->
```haskell
example = 84
```


### Every expression has a type
`intVal` is a word-sized integer
```haskell
intVal :: Int -- the variable intVal has the type Int
intVal = 31 * (42 * 56) 
```

`ii` is an Arbitrarily large number
```haskell
ii :: Integer
ii = 31 * (42 * 5600000 * 1000)
```

`dbl` is a double precision floating point
```haskell
dbl = 3 * (4.2 + 5.6)
```

# References
