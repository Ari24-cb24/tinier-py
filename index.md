# tinier-py
A collection of tricks to help you code golfing with Python or to confuse your code reviewers.

I use these python tricks all the time when clashing in shortest mode on codingame or playing code golf. These are very useful. If you want to add another snippet, create a pull request. Also, it would be very nice to help sorting that unsorted stuff or just correcting english grammar (mine is not so good, I'm not a native speaker).

Also, it's highly inspired by https://tinier.js.org/. I did not find any type of collection out there for python so I made one.

# Table Of Contents

- [tinier-py](#tinier-py)
- [Table Of Contents](#table-of-contents)
  * [What is Python/Code Golfing](#what-is-python-code-golfing)
  * [Why and when should minified code be used?](#why-and-when-should-minified-code-be-used-)
  * [General tricks](#general-tricks)
    + [Use of spaces around mathematical operators, strings and parantheses](#use-of-spaces-around-mathematical-operators--strings-and-parantheses)
    + [Indentations](#indentations)
  * [Reading inputs](#reading-inputs)
    + [Shorthand for reading inputs from stdin](#shorthand-for-reading-inputs-from-stdin)
    + [Reading inputs by defining a variable with the input function](#reading-inputs-by-defining-a-variable-with-the-input-function)
  * [Mathematics](#mathematics)
    + [Check for prime](#check-for-prime)
    + [Swapping out ``==`` with ``<``](#swapping-out--------with------)
    + [Shorthand for ``math.sqrt``](#shorthand-for---mathsqrt--)
    + [Flooring and Ceiling a float divided by another float](#flooring-and-ceiling-a-float-divided-by-another-float)
    + [Checking if float is an integer or a decimal](#checking-if-float-is-an-integer-or-a-decimal)
  * [Printing](#printing)
    + [Printing a string depending on a boolean](#printing-a-string-depending-on-a-boolean)
    + [Shorthand for using input instead of print](#shorthand-for-using-input-instead-of-print)
    + [Printing two integers with a space between them](#printing-two-integers-with-a-space-between-them)
    + [Printing decimal numbers without a zero if it's an integer](#printing-decimal-numbers-without-a-zero-if-it-s-an-integer)
    + [Shorthand for using ``join`` in a print statement](#shorthand-for-using---join---in-a-print-statement)
    + [Starred expressions in print functions](#starred-expressions-in-print-functions)
  * [Lists and Iterators/Generators](#lists-and-iterators-generators)
    + [Comparing two successive elements in a list](#comparing-two-successive-elements-in-a-list)
    + [Shortcut for using the ``list`` function on iterators like ``map``](#shortcut-for-using-the---list---function-on-iterators-like---map--)
    + [Assigning variables to a to list converted iterator](#assigning-variables-to-a-to-list-converted-iterator)
    + [Getting the last/first element of a list](#getting-the-last-first-element-of-a-list)
    + [Popping the last/first element of a list](#popping-the-last-first-element-of-a-list)
    + [Don't use the list method everywhere](#don-t-use-the-list-method-everywhere)
  * [For-loops](#for-loops)
    + [Combining two for-loops into one](#combining-two-for-loops-into-one)
    + [Shorthand for range(3)](#shorthand-for-range-3-)
    + [Shortcut for any range when the current iteration count is not important](#shortcut-for-any-range-when-the-current-iteration-count-is-not-important)
    + [Replacing For-Loops entirely with ``eval``](#replacing-for-loops-entirely-with---eval--)
  * [Regex](#regex)

## What is Python/Code Golfing

## Why and when should minified code be used?

> The purpose of code golfing is to test one’s abilities, during challenges. That said, you should not use techniques like this in your normal code, as it compromises readability. Ideally, you should only use these tricks during a challenge.  

<i> ~ tinier.js.org </i>

## General tricks


### Use of spaces around mathematical operators, strings and parantheses

The main goal is to save as much characters as possible. Some Code Golfing competitions like **clash of code** actually support a neat shortcut for saving spaces, e.g. in the following scenarios:

```py
[c if 1 == 1 else "0" for c in "Hello World!"]
```

this can be shorten to

```py
[c if1==1else"0"for c in"Hello World!"]
```

This is already pretty neat and a nice advantage. But speaking in general, you shouldn't have spaces around mathematical operators, strings and parantheses. For example

```py
print ( "Hello" + " " + "World" )
```

should **not** be done an can be written as

```py
print("Hello"+" "+"World")
```

or even better:

```py
print("Hello World")
```

### Indentations

Python gives you the abillity to use 1space instead of 4space. This can be seen in this example:

```py
for x in range(10):
	print(1)
```

As seen above, there is a tab-indentation used. This can take up to 4 characters. By using

```py
for x in range(10):
 print(1)
```

this you save 3 whole characters. If you have the possibillty, use

```py
for x in range(10):print(1)
```

as well to save another 2 characters!

## Reading inputs

### Shorthand for reading inputs from stdin

Let's say for example you have three lines of the given input e.g.
```mkd
10
20
30
```

normally, you would write something like

```py
# Longhand
a=int(input())
b=int(input())
c=int(input())
```

in order to retrieve all three of these numbers.
This can be minified by using ``open`` with the file descriptor ``0`` which stands for ``stdin``:

```py
# Shorthand
a,b,c=map(int,open(0).read().split())
```

``open(0)`` collects everything from the standard input. Its the same as reading a normal file in python. ``map`` is used here to instantly convert these inputs to integers.

### Reading inputs by defining a variable with the input function

If you have at least three inputs, you have the abillity to shorten your function calls in characters. This

```py
# Longhand
a=int(input())
b=int(input())
c=int(input())
```

can be shortened to

```py
# Shorthand
I=input
a=int(I())
c=int(I())
d=int(I())
```

## Mathematics

### Check for prime

A typical check for prime you see on the internet is e.g.

```py
# Longhand
if num > 1:
   for i in range(2,num):
       if (num % i) == 0:
           print(num,"is not a prime number")
           break
   else:
       print(num,"is a prime number")
else:
   print(num,"is not a prime number")
```

This can be easily written in an onliner:

```py
# Shorthand
print([i for i in range(2,num)if(num%i<1)]==[]and num>1)
```

### Swapping out ``==`` with ``<``

This is quite simple but I've seen countless people forget this. Swap out your equal equal by using a less than symbol:

```py
# Longhand
a==0

# Shorthand
a<1
```

This saves **a lot**! A character is much worth in code golfing.

### Shorthand for ``math.sqrt``

Instead of using ``math.sqrt``:

```py
# Longhand
import math
math.sqrt(int(input()))

# Shorthand
int(input())**0.5
```

### Flooring and Ceiling a float divided by another float

The math library has two functions: ``floor`` and ``ceil``:

```py
# Longhand
import math

a = float(input())
print(math.floor(a/3))
print(math.ceil(a/3))
```

tho we can make use of some simple math to shorten this:

```py
# Shorthand
a = float(input())
print(a//3))
```

> TODO: find shortcut for ceil, I remembered something like ``print(-(a//3))`` but I can't remember anymore lol

### Checking if float is an integer or a decimal

When checking for an integer, we can compare the floored and the ceiled outcome of the number.

```py
import math
a = float(input())

# Longhand
print(math.floor(a) == math.ceil(a))

# Shorthand by using modulo operator
print(a%1==0)
```


## Printing

### Printing a string depending on a boolean

Let's assume we have to print ``true`` when 1 is less than 2, otherwise we have to print ``false``. This could be solved by writing

```py
print(str(1<2).lower())
```

this already a short solution. The problem is that sometimes, you don't have to print ``true`` or ``false`` but instead something like ``wrong`` or ``right``. If you need to do that, mix both strings with each other and start with the longer string. E.g.
  
``wrong`` and ``right`` gets to ``wrriognhgt``.  
  
This may seem weird as first but we make use of the python string slicing function which gives us the abillity to skip certain indecies:

```py
print('wrriognhgt'[1<2::2])
```

If the output seems kinda wrong, mix the string again but this time start with the other part.

### Shorthand for using input instead of print

If you have 2 input statements and one print statement:

```py
# Longhand

a=input()
b=input()
print(a+b)
```

you can simplify that to:

```py
# Shorthand

I=input
a=I()
b=I()
I(a+b)
```

### Printing two integers with a space between them

This one is also an easy one. If you need to print two integers with a space in between, you could do:

```py
# Longhand
print(str(a//b) + " " + str(b//a))
```

but we can use multiple arguments in python which are splitted by a seperator:

```py
# Shorthand
print(a//b,b//a)
```

### Printing decimal numbers without a zero if it's an integer

These things can take up a lot of characters of code when you don't know a shortcut for it. The challenge states that we should print the float when there is a number after the decimal point, otherwise just print the number itself without the decimal point and the leading zero. A way to do this would be:

```py
# Longhand

my_float = str(...)

print(my_float.split(".")[0] if my_floats.endswith(".0") else my_float)

```

but a good shortcut for this would be to use Pythons Percentage formatting:

```py
# Shorthand
print("%g"%(my_float))
```

### Shorthand for using ``join`` in a print statement

If you need to seperate a list of numbers, don't use join:

```py
# Longhand
print(', '.join(['A', 'B']))
```

use a starred expression and the ``sep`` argument of the print function

```py
# Shorthand
print(*['A','B'],sep=', ')
```

### Starred expressions in print functions

As already mention above, you can use starred expressions in print statements to unpack every number of an interable or geneartor. Normally, this would seem like:


```py
# Longhand
print(" ".join(map(..., [0,1,2,3,4,5,6])))
```

but you can add an asterik before the ``map`` method which unpacks every value. (Also, you can map iterators as well)

```py
# Shorthand
print(*map(...,range(7)),sep=" ")
```

## Lists and Iterators/Generators

### Comparing two successive elements in a list

You can achieve this by writing

```py
# Longhand
l1 = [1, 2, 3, 4, 5]

for i in range(len(l1)):
	if i != len(l1) - 1:
		val1 = l1[i]
		val2 = l1[i+1]
```

but a much much shorter way of this would be by using the ``zip`` method, which returns a list containing tuples:

```py
# Shorthand
l1 = [1, 2, 3, 4, 5]

for val1, val2 in zip(l1, l1[1:])
```

### Shortcut for using the ``list`` function on iterators like ``map``

Converting an iterator like ``map`` to a list can be achieved by

```py
# Longhand
list(map(...))

# Shorthand by using starred expressions
[*map(...)]
```

### Assigning variables to a to list converted iterator

Let's say you need a list of the numbers in a range from 0 to 2, you could use range(3) and convert it to a list:

```py
A = list(range(3))
```

but again, there are these wonderful starred expressions:

```py
*A=range(3)
```

### Getting the last/first element of a list

Retrieving the last element can be done by accessing the negative one index

```py
# Longhand
L = [1, 2, 3, 4]
a=L[-1]
```

but we can just use the starred expression here again:

```py
# Shorthand for the last element
L = [1, 2, 3, 4]
*_,a=L
```

this can also be done as well for the first element:

```py
# Shorthand for the first element
L = [1, 2, 3, 4]
a,*_=L
```

### Popping the last/first element of a list

Python has gotten the pop method. This example is a bit bad but I think you can think of a use case

```py
L = [1, 2, 3, 4]

# Longhand
L.pop(0)

# Shorthand
# Popping the first index
_,*L=L

# Removing the last index
*L,_=L
```

what we do here is unpacking the list ``L`` to the variables ``_`` and ``L``. The underscore stands for a non-used variable.

### Don't use the list method everywhere

When having the following code

```py
# Longhand
print(sum(list(map(lambda e:e+1,[1,2,3,4,5,6]))))
```

you can remove the list function. ``sum`` can also sum iterators as well! And also, you might be noticing that the ``__add__`` method is used instead of a lambda. This is also shorter as well.

```py
# Shorthand
print(sum(map(int(1).__add__,[1,2,3,4,5,6])))
```

## For-loops

### Combining two for-loops into one

Combine two foor loops into one:

```py
# Longhand
for x in range(a):
	for y in range(b):
		print(x, y)

# Shorthand
for xy in range(a*b):
	x = xy//a
	y = xy%a
```

### Shorthand for range(3)

```py
# Longhand
for x in range(3):
	print(x)

# Shorthand
for x in 0,1,2:
	print(x)
```

### Shortcut for any range when the current iteration count is not important

```py
# Longhand
for _ in range(10):
	print(1)

# Shorthand
for _ in[1]*10:
	print(1)
```
<hr />

### Replacing For-Loops entirely with ``eval``

You can replace a for loop with a range when the current iteration count does not matter with the use of the ``eval`` function.

```py
# Longhand
for _ in range(n):
	print(1)

# Shorthand
exec('print(1);'*n)
```
<hr />

## Regex


# collection of unsorted stuff


```py
word = input()

print([c for c in word if c.isupper()])
```
can be written as
```py
import re
word=input()
print(re.sub('[^A-Z]','',word))
```
<hr />


```py
print(x == 5 and y == 6)
```
can be written as
```py
print((x,y)==(5,6))
```
<hr />
