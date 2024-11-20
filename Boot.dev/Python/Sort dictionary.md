1. filter keys to get only letters(line 23)
2. sort by value, reversed

```python
lowered_string = string.lower()
    result = {}
    for character in lowered_string:
        if character.isalpha():
            if character in result:
                result[character] += 1
            else:
                result[character] = 1
    result = dict(sorted(result.items(), key=lambda item: item[1], reverse=True))
    
    return result

```


Convert your dictionary of characters into a list of dictionaries and then use the [.sort()](https://docs.python.org/3/library/stdtypes.html#list.sort) method to sort by the number of occurrences. Here's an example:

```python
# A function that takes a dictionary and returns the value of the "num" key
# This is how the `.sort()` method knows how to sort the list of dictionaries
def sort_on(dict):
    return dict["num"]

vehicles = [
    {"name": "car", "num": 7},
    {"name": "plane", "num": 10},
    {"name": "boat", "num": 2}
]
vehicles.sort(reverse=True, key=sort_on)
print(vehicles)
# [{'name': 'plane', 'num': 10}, {'name': 'car', 'num': 7}, {'name': 'boat', 'num': 2}]
```

You can use a string's [.isalpha()](https://docs.python.org/3/library/stdtypes.html#str.isalpha) method to check if a string only contains characters from the alphabet.

