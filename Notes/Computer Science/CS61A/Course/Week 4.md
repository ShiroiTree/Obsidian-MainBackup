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