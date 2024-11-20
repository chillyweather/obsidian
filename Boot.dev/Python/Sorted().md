The `sorted()` function in Python is used to sort a list (or any iterable) and returns a new sorted list, leaving the original list unchanged. Here's how you can use the `sorted()` function for a list:

### Basic Usage

```python
Copy code

`# A list of numbers
numbers = [5, 2, 9, 1, 5, 6]

# Sorting the list in ascending order
sorted_numbers = sorted(numbers)

print("Original list:", numbers)
print("Sorted list:", sorted_numbers)` 
```

### Sorting in Descending Order

To sort in descending order, you can use the `reverse` parameter and set it to `True`:

```python

Copy code

# Sorting the list in descending order
sorted_numbers_desc = sorted(numbers, reverse=True)

print("Original list:", numbers)
print("Sorted list in descending order:", sorted_numbers_desc)
```` 

### Sorting a List of Strings

```python

Copy code

# A list of strings
fruits = ["apple", "orange", "banana", "pear"]

# Sorting the list of strings in alphabetical order
sorted_fruits = sorted(fruits)

print("Original list:", fruits)
print("Sorted list:", sorted_fruits)` 
```

### Sorting with a Custom Key Function

You can also provide a custom key function to determine the sorting criteria. For example, sorting a list of tuples based on the second element:

```python

Copy code

# A list of tuples
tuples = [(1, 'one'), (3, 'three'), (2, 'two')]

# Sorting the list of tuples based on the second element
sorted_tuples = sorted(tuples, key=lambda x: x[1])

print("Original list:", tuples)
print("Sorted list based on second element:", sorted_tuples)
```` 

### Sorting by String Length

Here's an example of sorting a list of strings based on their lengths:

```python

Copy code

# A list of strings
words = ["banana", "pie", "Washington", "book"]

# Sorting the list by the length of the words
sorted_words_by_length = sorted(words, key=len)

print("Original list:", words)
print("Sorted list by length:", sorted_words_by_length)` 
```

### Summary

- `sorted(iterable)` sorts in ascending order.
- `sorted(iterable, reverse=True)` sorts in descending order.
- `sorted(iterable, key=some_function)` sorts based on a custom key function.

Each of these examples illustrates how to use the `sorted()` function to achieve different kinds of sorting for a list.