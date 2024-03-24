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
## Q&A
### Frame
A memory where the computer keeping track of what names mean. In somehow, it's like Namespace in C++.
There are two frames, global frame and function-call frame.
When a function is called, a frame is created to store information such as local variables, parameters, and the return address.
### Assignment Statements
If you wrote someting below.
```
a = 1
b = 2
b, a = a + b, b
```
The result is a=2 and b=3.
Execution rule for assignment statements:
	1.Evaluate all experssion to the right of = from left to right.
	2.Bind all names to the left of = to those resulting values in the current fram