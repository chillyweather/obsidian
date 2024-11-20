# CURRYING

Function [currying](https://en.wikipedia.org/wiki/Currying) is just a specific type of function transformation. It's when we translate a function that takes multiple arguments into a sequence of functions, each with a single argument.

For example, take this simple function:

```py
def sum(a, b):
  return a + b

print(sum(1, 2))
# prints 3
```

We can curry this function into a sequence of functions that each take a single argument:

```py
def sum(a):
  def inner_sum(b):
    return a + b
  return inner_sum

print(sum(1)(2))
# prints 3
```

The `sum` function only takes a _single_ input, `a`, and returns a _new_ function that takes a single input, `b`. This new function when called with a value for `b` will return the sum of `a` and `b`.

We've taken a function that operates on two _different_ parameters and created a series of functions that operate on _one_ parameter each.