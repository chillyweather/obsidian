## Example 1

```python
def list_files(current_node, current_path=""):
    list_o_path = []
    for element in current_node:
        new_path = f"{current_path}/{ element }"
        if current_node[element] is None:
            list_o_path.append(new_path)
        else:
            list_o_path.extend(list_files(current_node[element], new_path))

    return list_o_path
```

