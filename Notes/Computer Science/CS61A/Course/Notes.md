# Lecture 01 Computer Science
## About the course
Lab is the most important part of this course.
## An Introduction to Computer Science
### What is Computer Science
The study of how to solve problems through computers, what technques lead to effective solutions.
Including System, Artificial Intellignece, Graphics, Programming Languages. And there are a mount of sub-fields in these fields.
### It's a course about managing comlexity.
Mastering abstraction
Programming paradigms

The high productivity of computer science is only possible because the discipline is built upon an elegant and powerful set of fundamental ideas. All computing begins with representing information, specifying logic to process it, and designing abstractions that manage the complexity of that logic. Mastering these fundamentals will require us to understand precisely how computers interpret computer programs and carry out computational processes.
One of the powerful fundamental ideas is abstraction, which allow users only need to know how to use but no need to konw how it works.
## Functions, Values, Objects, Interpreters, and Data
### About programming 
Programs must be written for people to read, and only incidentally for machines to execute.

Every powerful language has three such mechanisms:
- **primitive expressions and statements**, which represent the simplest building blocks that the language provides
- **means of combination**, by which compound elements are built from simpler ones
- **means of abstraction**, by which compound elements can be named and manipulated as units

# Lecture 02 Functions
## Expressions
### What is expression
An expression describes a computation and evaluates to a value.
### Type of expression
Primitive expression : Number Name String
Call expression : Operator ( Operand , Operand )
## Environment Diagrams
Environment diagrams visualize the interpreter's process, which help us to understand how programs get executed.
## Assignment Statements
Assignment statements bind all names to the letf of = to the resluting values in the current frame. Assignment statements can bind names to values, names to functions or even rebind an existed function name to a new value.
==Once you want to bind a function to a new name, only the name is necessy, but Operand.==
## Defining Functions
Assignemnt is a simple means of abstraction: binds names to valuse.
Function definition is a more powerful means of abstraction: binds names to expressions.
```
def <name>(<formal parameters>):
	return <return expression>
```
The function won't be exectued once been called.
## Names in Environments
Every expression is evaluated in the context of an envirment.
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
# Lecture 06 Design
## Abstracions
```
def square(x):
	return mul(x, x)

def sum_square(x, y):
	return square(x) + square(y)
```
**What does sum_square need to know about square in order to use it correctly?**
* Square takes one argument.---Yes
* Square has the intrinsic name square.---No
* Square computes the square of a number.---Yes
* Square computes the square by calling mul.---No
### Choosing Names
Name typically don't matter for correctness but they matter a lot for composition
1. Names should convey the meaning or purpose of the values to which they are bond.
2. The type of value bound to the name is best document in a function's docstring.
3. Functions names typically convey their effect, their behavior, or the value returned.
However, the main idea of choosing names is a name should help user to understand what the name bound to, what dose it for.
## What's the point of higher-order functions?
### Example: Sounds

# Lecture 07 Function Examples
This Lecture is about some examples of higher order functions, nothing to write.
# Lecture 08 Recursion
## Recursive Functions
**Definition:** A funtion is called recursive if the body of that function calls itself, either directly or indirectly.
## The Recursive Leap of Faith
```
def fact(n):
	if n == 0:
		return 1
	else:
		return n * fact(n-1)
```
**Is fact implemented correctly?**
1. Verify the base case.
2. Treat fact as a functional abstraction!
3. Assume that fact(n-1) is correct.
4. Verify that fact(n) is correct, assuming that fact(n-1) is correct.
## Mutual Recursion
### The Luhn Algorithm
```
def split(n):
	return n // 10, n % 10

def sum_digits(n):  //Recursive Function
	if n < 10:
		return n
	else:
		all_but_last, last = split(n)
		return sum_digits(all_but_last) + last

def luhn_sum(n):  //Mutual Recursion
	if n < 10:
		return n
	else:
		all_but_last, last = split(n)
		return luhn_sum_double(all_but_last) + last

def luhn_sum_double(n):
	all_but_last, last = split(n)
	luhn_digit = sum_digits(2 * last)
	if n < 10:
		return luhn_digit
	else:
		return luhn_sum(all_but_last) + luhn_digit
```
In this case, the luhn_sum_double() and the luhn_sum() called each other. So that is Mutual Function.
## Converting Recursion to Iteration
**Can be tricky:** Iteration is a special case of recursion.
**Idea:** The state of an iteration can be passed as arguments.
```
def sum_digits_iter(n):
	digit_sum = 0
	while n > 0:
		n, last = split(n)
		digit_sum = digit_sum + last
	return digit_sum

def sum_digits_rec(n, digit_sum)
	if n == 0:
		return digit_sum
	else:
		n, last = split(n)
		return sum_digit_rec(n, digit_sum + last)

```
Here is how an iteration turn to a recusive function.
# Lecture 9 Tree Recursion
## Order of Recursive Calls
The point is that, when you called one function, you must to wait for return.
## Tree Recursion
Tree recursion happens when one function makes more than one recursive call.
### Example: fib()
```
def fib(n):
	if n == 0:
		return 0
	elif n == 1:
		return 1
	else:
		return fib(n-1) + fib(n-2)
```
The computational process of fib evolves into a tree structure. More precific in this case, it's binary tree. How the functions were called is fit pretrauersal of a binary tree. You can use *@trace* to creat a tree to understand how it works.
### Example: Counting Partitions
The number of partitions of a positive integer n, using parts up to size m, is the number of ways in which n can be experessed as the sum of positive integer parts up to m, in increasing order.
```
def count_partitions(n, m):
	if n == 0:
		return 1
	elif n < 0:
		return 0
	elif m == 0:
		return 0
	else:
		with_m = count_partitions(n-m, m)
		without_m = count_partitions(n, m-1)
		return with_m + without_m
```