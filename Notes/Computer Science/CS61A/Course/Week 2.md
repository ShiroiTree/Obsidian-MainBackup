# Lecture 03 Control
## Print and None
Here is an interesting case:
```
>>>print(print(1),print(2))
1
2
None,None
```
### None
None indicates that nothing is returned.
### Pure Functions and Non-Pure Functions
Pure Functions: Just return values.
	Likes max() abs()
Non-Pure Functions: Have side effects.
	Likes print()
Here's what's going on in that case.
## Multiple Environments
### Call frame
Once a function was called, a new frame is created.
An envirment is a sequence of frames.
## Miscellaneous Python Features
### How operator works
Behave like bulit in function calls.
### Division
#### Truediv and Floordiv
Which is / and //.
## Conditional Statements
A statement is executed by the interpreter to perform an action.
# Lecture 04 Higher-Order Functions
## Designing Functions
There're a lot fo function, but some of them are better than other, because they are more useful in more situation.
A function's domain and range decided where it can be used.
### A Guide to Designing Function
Give each function exactly one job.
Don't repeat yourself. Implement a process just once, but execute it mant times.
Define function generally.
## Higher-Order Functions
### Generalizing Patterns with Arguments
If you have a pattern repeating in your code, you can generalizing them into one function. Then you can use it as an argument in your expession.
```
def sum_naturals(n)
	total, k = 0, 1
	while k <= n:
		total, k = total + k, k + 1
	return total
	
def sum_cubes(n):
	total, k = 0, 1
	while k <= n:
		total, k = total + pow(k, 3), k + 1
	return total
```
We generalizing the main code as followed.
```
def ifentity(k):
	return k

def cube(k):
	return pow(k, 3)

def summation(n, term):
	total, k = 0, 1
	while k<=n:
		total, k = total + term(k), k+1
	return total

def sum_naturals(n):
	return summation(n, ifentity)

def sum_cubes(n):
	return summation(n, cube)
```
However some code like that are only availib on python, since only python can transmit a function name as an argument.
Functions defined within other function bodies are bound to names in a local frame.
### Function as Return Values
Here is an examlp.
```
def make_adder(n):
	def adder(k):
		return k + n
	return adder
```
Functions defined within other function bodies are bound to names in a local frame.
You can use this code as follow.
```
>>> make_adder(1)(2)
3
>>> f = make_adder(1)
>>> f(2)
3
```
Which, bind a name to a new function.
### The Purpose of Higher-Order Functions
**Functions are first-class:** Functions can be manipulated as valuse in our programming language.
**Higher-order function:** A function that takes a function as an argument value or returns a function as a return value.
Higher-order functions:
* Express general methods of computation
* Remove repetions from programs
* Separate concerns among functions
## Lambda Expressions
Lambda expression present as follow.
```
square = lambda x: x * x
```
## Return
A return statement completes the evaluation of a call experssion and provides its value/
Only one return statement is ever executed while executring the body of a function.
```
def search(f):
	x = 0
	while True:
		if f(x):
			return x
		x += 1

def square(x):
	return x * x

def positive(x):
	return max(0, square(x) - 100)

>>> search(positive)
11
```
# Lecture 05 Environments
## Envirments for Higher-Order Functions
To be simple, the way varible bind to function or value in python is differet that in C/C++. In python, the interpreter takes the name as a sign, but don't really care what it is. But in C/C++, the interpreter takes the name as a pointer which point to a specific object.
### Example
#### Repeat
```
def repeat(f, x):
	while f(x) != x:
		x = f(x)
	return x

def g(y):
	return (y + 5) // 3
```

```
def make_adder(n):
	def adder(k):
		return k + n
	return adder
```
In this case, we can find someting ineresting.The function adder has a frame called f1, which bind to a function.
When the inner function been called, the interpreter will look first in the first frame of the current environment, then is the second which is the parent of the first frame and so on.
* Every user-defined function has a parent frame (often global)
* The parent of a function is the frame in which it was defined
* Every local frame has a parent frame
* The parent of a frame is the parent of the function called
Also we can compose functions together using Higher-Order funcrion.
```
def square(x):
	return x*x

def make_adder(n):
	def adder(k):
		return k + n
	return adder

def compose1(f, g):
	def h(x):
		return f(g(x))
	return h

compose1(square, make_adder(2))(3)
```
