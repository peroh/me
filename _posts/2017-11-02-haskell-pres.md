---
layout: page
title: "Haskell Presentation"
short: "blah blah  blah"
sidebar: true
sidebar_position: right
image: "/images/banner.jpg"
---

# Haskell Presentation

## Programming Paradigms

* Imperative
    * Procedural
    * Object oriented
* Declarative
    * Functional
    * Logic

Imperative - sequence of tasks to execute, and while executing, things
change state.

Declarative - say what stuff is. In functional programming, we describe things
with functions.

## Functional Programming

What should our mindset be?

* Start to think about functions like they're variables. We use them everywhere as easily as we use a variable.
* Functions are kind of the same thing as data
* Functions have types!
* Functional programming is really just a style. We can program functionally in imperative langauges.
* Think "nouny" not "verby"
* Recursion is KING

What is a function?

* Has inputs and outputs
* Referentially transparent

## Haskell

1. **Purely functional** - no side effects! Has referential transparency. Only have to look at a function, not the whole program. Good for concurrency.
2. **Lazy** - only evaluates things when it needs to. Allows infinite lists, data structures become generators.
3. **Statically typed with type inference** - types must match up at compile time. Haskell can guess what type you want.

## GHCI

Glasgow Haskell Compiler is most widely used compiler for Haskell.

The interpreter can load haskell scripts (.hs) and allows interactivity.

```bash
$ ghci
> 3 + 2
> 3 - 2
> 3 * 2
> 3 / 2
> 3 * (-2) # need the parens
> (3 + 2) * 2 # can use parens to change precedence
```

## Prelude

You'll notice that commands in GHCI start with Prelude. This is Haskell's
standard library.

Some common functions in the Prelude.

* head
* tail
* init
* last
* length
* take
* drop
* elem
* zip
* map
* filter

## Lists

Think of them as linked lists, not arrays.

All elements of a list must be of the same type.

```bash
> []      # empty list
> [3]     # singleton list
> 3:[]    # singleton list
> [2,3]   # 2-element list
> 2:[3]   # 2-element list
> 2:3     # CAN'T do this
> 2:3:[]  # can we do this then? YES!
```



## Defininig Functions

```haskell
doubleMe x = x + x
addMe x y = x + y
isEqual x y = x == y
```

## Exercise - Scripts

Haskell scripts have the extension `.hs`.

1. Create a file in your current directory called ex1.hs
2. Write a function `addTwo` which adds 2 to it’s input. Save.
3. Start GHCi with `ghci`
4. Load file with `:l ex1.hs`
5. Call your function

## Pattern Matching

Specifying pattern to which data should conform
Define seperate functions bodies for different patterns
Can pattern match on any data type
Goes through patterns line by line, top-down

```haskell
addTwo 0 = 1
addTwo x = x + x
```

## Types

Haskell has a strong, safe and static type system.

Type signatures

```haskell
addMe :: Int -> Int -> Int
addMe x y = x + y
```

Type variables

```haskell
length :: [a] -> Int
```

## Exercise

Given the following functions and their type signatures, use ghci to work out what the following prelude functions do.

```haskell
succ :: Int -> Int
head :: [a] -> a
tail :: [a] -> a
max :: Int -> Int -> Int
maximum :: [a] -> a
not :: Bool -> Bool
```

## More on Types

Checking a type:

```bash
> :t not
not :: Bool -> Bool
```

New construct, type class:

```bash
> :t (+)
(+) :: Num a => a -> a -> a

> :t max
max :: Ord a => a -> a -> a
```

Some type classes:

* Num
* Ord
* Eq
* Foldable

## Strings

Strings are just a list of Chars. This means we can perform list operations
on strings.

```bash
> ['w','o','r','d']
"word"
```

## Infix vs Prefix Operators


## Exercise

Implement the logical XOR function using pattern matching.

```haskell
xor_pattern :: Bool -> Bool -> Bool
xor_pattern False False = False
xor_pattern True True = False
xor_pattern False True = True
xor_pattern True False = True
```

Could we reduce the number of lines?

Now think of a smarter way to implement it, using another prelude function.

```haskell
xor :: Bool -> Bool -> Bool
xor x y = not (x == y)
```

## More pattern matching

We can match by an arguments **structure**, not just it's value.

Can use the cons operator to match a list, but assigning a different variable
name to the head and tail of the list.

Can also match for an empty list, or a singleton list.

```haskell
length' :: [a] -> Int
length' [] = 0
length' [x] = 1                       -- this line is not relevant
length' (x:xs) = 1 + length' xs
```

This pattern is very common.

Notice we don't use the `x`, can drop it and use `_`.

## Recursion

Since we don't have a looping construct in Haskell, we often need to utilise
recursion.

* Base case
* Recursive case

Sometimes easiest to write recursive case first and just placeholder the base case.

```haskell
append :: [a] -> [a] -> [a]
-- Base case
append [] ys = ys
-- Recursive case
append (x:xs) ys = x : append xs ys
```

Step by step execution of `append [1,2] [3,4]`:

--     Initial           -- Pattern         -- Result
append [1,2] [3,4] = append 1:[2] [3,4] = 1 : append [2] [3,4]

append [2] [3,4]   = append 2:[] [3,4]  = 2 : append [] [3,4]

append [] [3,4]    = append [] [3,4]    = [3,4]

1:2:[3,4] = [1,2,3,4]

## Exercises

Write a function to calculate the factorial.

Think about:

* Using a base and recursive case
* What the base case should pattern match on

```haskell
factorial :: Int -> Int
factorial 0 = 1
factorial n = n * factorial (n-1)
```

Write a function to sum a list of Integers

```haskell
sumlist :: [Int] -> Int
sumlist [] = 0
sumlist (x:xs) = x + sumlist xs
```

Write a function to reverse a list using recursion and the (++).

```haskell
reverse' :: [a] -> [a]
reverse' [] = []
reverse' (x:xs) = reverse' xs ++ [x]
```

## Guards

We don't have to just use pattern matching. We can use an if-then-else
construct.

```haskell
elem' :: a -> [a] -> Bool
elem' x [] = False
elem' x (y:ys)
  | x == y = True
  | x /= y = elem' x ys
```

### Otherwise

Can replace `x /= y` with `otherwise` here. `otherwise` is just syntactic sugar
for `True`, and is used as a "catch-all".

## Higher Order Functions

A higher order function is a function that takes another function as an
argument.

One commonly used higher order function is `map`.

```haskell
map :: (a -> b) -> [a] -> [b]
```

```bash
> map (+2) [1,2,3]
[3,4,5]
> map even [1,2]
[False, True]
```

Defining map is easy

```haskell
map' :: (a -> b) -> [a] -> [b]
map' _ [] = []
map' f (x:xs) = f x : map' f xs
```

`_` used when we don't care about the argument.

Sidenote: Chars are enumerable

```bash
> map succ ['a', 'b']
"bc"
```

### Filter

Like map, but more restricted.

Function it takes is `a -> Bool`

```bash
> filter even [1,2,3,4]
[2,4]
```

## Tuples

Tuples are a collection of elements. The elements can be of any type, and the tuple forms its own type.

Tuples are defined in brackets and can be of any arity.

Tuple length/size:

* 0 - unit
* 2 - pair
* 3 - triple
* n - n-tuple

*1 - not supported without extra package*

```bash
> :t (1,2)
(1,2) :: (Num a, Num b) => (a, b)
> :t ('a', "bc", 3, 4.0)
('a', "bc", 3, 4.0) :: (Num t1, Fractional t) => (Char, [Char], t1, t)
> :t ()
() :: ()
```

## Lambda Functions

Haskell supports lambda calculus to write unnamed functions.

```bash
> (\x ->  x + 2) 2
4
> (\x y ->  x + 2 * y) 2 4
10
```

## List Comprehension

## Precedence

Brackets > Function application (juxtaposition) >

```bash
>
```

> map even [1,2,3]


## Example

**Create a list between min and max**

How would we do this in python?

```python
def listCreate(min, max):
  my_list = []
  while min <= max:
      my_list.append(min)
      min += 1
  return my_list
```

Let's take some of those concepts and transfer them to recursion.

```haskell
listCreate :: Int -> Int -> [Int]
listCreate minn maxx
 | minn > maxx = []
 | otherwise   = minn: listCreate (minn+1) maxx
```



We have to declare the Eq typleclass. Haskell doesn't wanna risk it!

```
myElem :: Eq a => a -> [a] -> Bool
myElem _ [] = False
myElem x (y:ys)
 | x == y    = True
 | otherwise = myElem x ys
```

Will both of these work?

```
ghci> myElem "ab" "dabc"
ghci> myElem 'ab' "dabc"
```

Let's write a subset method.

```
subset :: Eq a => [a] -> [a] -> Bool
subset [] _ = True
subset _ [] = False
subset (x:xs) y'@(y:ys)
 | x == y = subset xs ys
 | otherwise = subset xs y'
```

## Example

An example of translating C code to Haskell without necessarily understanding
the algorithm.

```c
int mccarthy_91(int n)
{
   int c = 1;

   while (c != 0) {
       if (n > 100) {
           n = n - 10;
           c--;
       } else {
           n = n + 11;
           c++;
       }
   }

   return n;
}
```

How do we set a variable?

```haskell
mccarthy91 :: Int -> Int
mccarthy91 n = mccarthy91' n 1

mccarthy91' :: Int -> Int -> Int
mccarthy91' n 0 = n
mccarthy91' n c
 | n > 100   = mccarthy91' (n-10) (c-1)
 | otherwise = mccarthy91' (n+11) (c+1)
```

## Example

Merge sorted lists

```haskell
merge :: Ord a => [a] -> [a] -> [a]
merge [] y = y
merge x [] = x
merge (x:xs) (y:ys)
 | x <= y    = x: merge xs (y:ys)
 | otherwise = y: merge (x:xs) ys
```

## Example

Quicksort (in-place)

```haskelll
quicksort :: Ord a => [a] -> [a]
quicksort [] = []
quicksort (pivot:rest) = (quicksort lowers) ++ [pivot] ++ (quicksort highers)
  where
    lowers  = filter (<pivot) rest
    highers = filter (>=pivot) rest
```

How would we remove duplicates?

```haskell
    ...
    highers = filter (>pivot) rest
```

## Good Resources

* LearnYouAHaskell
* Hoogle
* Standard 98 Report  - https://www.haskell.org/onlinereport/standard-prelude.html

## More Important Topics

* Data constructors, value constructors (and their arity)
* Monads
