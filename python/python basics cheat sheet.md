# Python Basics Cheat Sheet

**Table of Contents:**
* [Basic Operations](#basic-operations)
* [Conditions](#conditions)
* [Loops](#loops)
	* [While loop](#while-loop)
	* [For loop](#for-loop)
	* [Break & Continue](#break--continue)
* [Importing](#importing)
* [Common Functions](#common-functions)
	* [Range Function](#common-functions)
	* [Max & Min Functions](#max--min-functions)
* [Functions](#functions)
* [Random](#random)
		
## Basic Operations

The basic Operations are:

```python
x = a+b # Sum
x = a-b	# Subtract
x = a*b # Multiply
x = a/b # Division
x = a%b # Mod
x = a**b # Power
x = a//b # Int Division

x += a # Adds a to x
x -= a # Subtract a from x
x *= a # Multiply x by a
x /= a # Divid x by a
```


## Conditions
- We use (`if`, `elif`, `else`).
- Uses a boolean Expression.
- To compine multiple statments we use (`AND`, `OR`, `NOT`).
- To use comperison we use (`>`, `<`, `>=`, `<=`,`==`, `!=`).
- Examples:

	```python
	if x>y:
		print('x is bigger')
	elif x<y:
		print('y is bigger')
	else:
		print('x equals y')
	```


## Loops

Use loops to repeat a block of code multiple times:

### While loop
- Similar to if Condtion uses a boolean expression to loop.
- Had else statment works when the loop breaks.
- Examples:

	```python
	# This program will print the numbers form 0 to 9
	# Then when the loop breaks "done" will be printed

	i = 0 # counter for the loop
	while i < 10:
		print(i)
		i += 1
	else:
		print('done')
	```

### For loop
for loop similar to while but works on different data types:
- Strings:

	```python
	# The variable (i) will iterate on the String characters
	# This loop will print the string vertically

	for i in "this is some string": 
		print(i)
	```

- Lists & Tuples:

	```python
	# The variable (i) will iterate on the List items
	for i in [1,'a',True,'Hi']:
		print(i)

	# The variable (i) will iterate on the Tuple items
	for i in (1,'a',True,'Hi'):
		print(i)
	```

	more about [Tuples](/python/python%20tuples) & [Lists](/python/python%20lists.md).


- Ranges:

	```python
	# The variable (i) will iterate on range from 0 to 9
	for i in range(10):
		print(i)
	```

	more about [Range Function](#range-function)

### Break & Continue

- Use `break` keyword to break from a loop.
- Use `continue` keyword to return to the start of the loop and continue.


## Importing
To use External Modules:

- Importing function :

```python
import math
import ....
```

-Using From:

```python
from math import factorial
from .... import .........
from math import *
from .... import *
```

- You can also use:

```python
import math as m # m.factorial()
from math import factorial as f	# f()
```

## Common Functions

Some Common & Useful functions you should know.


### Range Function

Used to create Ranges:

```python
range(n)		# it will make a range from 0 to n-1
range(a,b)		# it will make a range from a to b-1
range(a,b,c)	# it will make a range from a to b-1 moving c steps 
```


### Max & Min Functions

Used to find max or min item in list or tuple:

```python
max(a,b)	# returns the maximum number
min(a,b)	# returns the minimum number
mylist = [2,4,56,1,2,4,6] # the list should have only same data type
print(max(mylist))	# Prints 56
print(min(mylist))  # Prints 1
```


## Functions

To Define a function:

```python
def Function_Name(Parameters):
	//TODO
```

The `argument` keyword:

```python
def print_first(v1,v2)
	print(v1)
	
print(print_first('Hello','World'))	# Prints Hello World
print(print_first('World','Hello'))	# Prints World Hello
print(print_first(v1 = 'Hello', v2 ='World')) # Prints Hello World
print(print_first(v2 = 'World', v 1 = 'Hello')) # Prints Hello World
```

The `return` function will return `None` by default.


## Random

Needs to import `random` module:

```python
import random
```

To get a random **double** number between 0 & 1:

```python
random.random()
```

To get a random number between 2 intgers a & b:

```python
random.randint(a,b)
```

To get a random item from a list:

```python
myList = [1, 2, 3, 4]
random.choice(myList)
```