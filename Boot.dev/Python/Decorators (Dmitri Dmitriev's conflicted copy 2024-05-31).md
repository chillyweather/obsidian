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


```python
def file_type_aggregator(func_to_wrap):
    # dict of file_type -> count
    counts = {}

    def wrapper(doc, file_type):
        nonlocal counts

        if file_type in counts:
            counts[file_type] += 1
        else:
            counts[file_type] = 1
        result = func_to_wrap(doc, file_type)

        return result, counts

    return wrapper


@file_type_aggregator
def process_doc(doc, file_type):
    return f"Processing doc: {doc} with File Type: {file_type}"
```

Inputs: ('Welcome to the jungle', 'txt')
Result: ('Processing doc: Welcome to the jungle with File Type: txt', {'txt': 1})