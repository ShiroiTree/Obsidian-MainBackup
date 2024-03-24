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
## Describing Functions