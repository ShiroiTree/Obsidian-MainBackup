# Lecture 10 Containers
## Lists
To creat a list, you can write like this. 
```
list = [1, 2, 3]
```
Concatenation and repetition
```
>>> digits = [1, 8, 2, 8]
>>> [2, 7] + digits * 2
[2, 7, 1, 8, 2, 8, 1, 8, 2, 8]
```
In for statement, for statement go through the list you give.
```
for <name> in <expression>:
<suite>
```
1. Evaluate the header \<expression\>, which must yield an iterable value (a sequence)
2. For each element in that squence, in order:
	1. Bind \<name\> to that element in the current frame
	2. Execute the \<suite\>
Range is a sequence of consecutive integers, which can help you creat a list.
```
>>> list(range(-2, 2))
[-2, -1, 0, 1]
```
Here's an example of list.
```
def mySum(l):
	if (l == []):
		return 0
	else
		return l[0]+mySum(l[1:])
```
## List Comprehensions
Here's an example.
```
>>> letter = ['a', 'b', 'c', 'd', 'e', 'f', 'm', 'n', 'o', 'p']
>>> [letters[i] for i in [3, 4, 6, 8]]
['d', 'e', 'm', 'o']
>>> odds = [1, 3, 5, 7, 9]
>>> [x+1 for x in odds]
[2, 4, 6, 8, 10]
>>> [x+1 for x in odds if 25 % x == 0]
[2, 6]
```
## Strings
Strings are an abstraction.
```
"Here is a string."
'Here is another string.'
```
A backslash "escapes" the following character.

# Lecture 11 Data Abstraction 
- Compound objectis combine objects together
- 