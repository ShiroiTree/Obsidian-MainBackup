# Lambda
## Examples
```
>>> higher_order_lambda = lambda f: lambda x : f(x)
>>> g = lambda x: x * x
>>> higher_order_lambda(2)(g)
Error
>>> higher_order_lambda(g)(2)
4
```
In the higher_order_lambda, the first lambda funtion is been used as a function in the second lambda function. So, if we want the code to execute correctly, the operand must be a function.