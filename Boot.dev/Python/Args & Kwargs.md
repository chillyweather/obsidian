In Python, `*args` and `**kwargs` allow a function to accept and deal with a _variable_ number of arguments.

- `*args` collects positional arguments into a _tuple_
- `**kwargs` collects keyword (named) arguments into a _dictionary_

```py
def print_arguments(*args, **kwargs):
    print(f"Positional arguments: {args}")
    print(f"Keyword arguments: {kwargs}")

print_arguments("hello", "world", a=1, b=2)
# Positional arguments: ('hello', 'world')
# Keyword arguments: {'a': 1, 'b': 2}
```

## POSITIONAL ARGUMENTS

Positional arguments are the ones you're already familiar with. They're the arguments that are passed in by position, like this:

```py
def sub(a, b):
    return a - b

res = sub(3, 2)

print(res)
# 1
```

## KEYWORD ARGUMENTS

[Keyword arguments](https://docs.python.org/3/tutorial/controlflow.html#keyword-arguments) are passed in by name, order does not matter. Like this:

```py
def sub(a, b):
    return a - b

res = sub(b=3, a=2)

print(res)
# -1
```

## A NOTE ON ORDERING

Any positional arguments _must come before_ keyword arguments. Python will try to match up the arguments you pass in with the arguments in the function definition by position first, and then by name.

This will _not_ work:

```py
sub(b=3, 2)
```