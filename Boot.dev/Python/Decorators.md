# DECORATORS

Decorators are a Python-specific way to modify or enhance existing functions. They're just Pythonic syntactic sugar for higher-order functions (and sometimes closures).

A function can be used as a decorator if it takes a function as an argument and returns a new function. The new function can then be used in _place_ of the original function. Again, this is typically used to modify or enhance the behavior of the original function.

## EXAMPLE: VOWEL COUNTER

```py
def vowel_counter(func_to_wrap):
    vowel_count = 0
    def wrapper(doc):
        nonlocal vowel_count
        vowels = "aeiou"
        for char in doc:
            if char in vowels:
                vowel_count += 1
        print(f"Vowel count: {vowel_count}")
        return func_to_wrap(doc)
    return wrapper

@vowel_counter
def process_doc(doc):
    print(f"Document: {doc}")

process_doc("Hello")
# Vowel count: 2
# Document: Hello

process_doc("world")
# Vowel count: 3
# Document: world
```

## WHAT'S THE BIG DEAL?

Decorators are just [syntactic sugar](https://en.wikipedia.org/wiki/Syntactic_sugar) for [higher-order functions](https://en.wikipedia.org/wiki/Higher-order_function). These two pieces of code are _identical_:

### WITH DECORATOR

```py
@vowel_counter
def process_with_count(doc):
    print(f"Document: {doc}")
```

### WITHOUT DECORATOR

```py
def process(doc):
    print(f"Document: {doc}")

process_with_count = vowel_counter(process)
```


If your decorator doesn't care about the specific arguments of the function it's decorating, then you can use the `*args` and `**kwargs` syntax to make it more generic.

## EXAMPLE: LOGGER

```py
def log_call_count(func_to_wrap):
    count = 0

    def wrapper(*args, **kwargs):
        nonlocal count
        count += 1
        print(f"Called {count} times")
        return func_to_wrap(*args, **kwargs)

    return wrapper

@log_call_count
def add_with_log(a, b):
    return a + b

res = add_with_log(2, 3)
# Prints: Called 1 times
res = add_with_log(4, 5)
# Prints: Called 2 times
```

## TIP

In addition to accepting arbitrary inputs in a function definition using the `*` and `**` syntax, you can also pass _in_ arbitrary inputs to a function call using a similar syntax. For example:

```py
def make_character(name, age, x, y):
    # ...

# This:
positional_args = ["Lane", 28]
keyword_args = {"x": 1, "y": 2}
make_character(*positional_args, **keyword_args)

# Is equivalent to this:
make_character("Lane", 28, x=1, y=2)
```

The `*` and `**` syntax _unpacks_ a list or dictionary into the arguments of a function call.


```python
def markdown_to_text_decorator(func):
    def wrapper(*args, **kwargs):
        converted_args = []
        for arg in args:
            converted_args.append(convert_md_to_txt(arg))
        for key, value in kwargs.items():
            kwargs[key] = convert_md_to_txt(value)
        return func(*converted_args, **kwargs)

    return wrapper


def convert_md_to_txt(doc):
    lines = doc.split("\n")
    for i in range(len(lines)):
        line = lines[i]
        lines[i] = line.lstrip("# ")
    return "\n".join(lines)


# Don't edit below this line


@markdown_to_text_decorator
def concat(first_doc, second_doc):
    return f"""First: {first_doc}
Second: {second_doc}
"""


@markdown_to_text_decorator
def format_as_essay(title, body, conclusion):
    return f"""Title: {title}
Body: {body}
Conclusion: {conclusion}
"""

```