A [closure](https://en.wikipedia.org/wiki/Closure_(computer_programming)) is a function that references variables from outside its own function body. The function definition _and its environment_ are bundled together into a single entity.

Sound confusing? Sorry. Put simply, a closure is just a function that retains access to some values from the place where it was _defined_, no matter where it is executed later on.

## EXAMPLE

The `concatter()` function returns a function called `inner_func` (yay higher-order functions!) that has a reference to an _enclosed_ `doc` value.

```py
def concatter():
	doc = ""
	def inner_func(word):
		# "nonlocal" tells Python to use the doc
		# variable from the enclosing scope
		nonlocal doc
		doc += word + " "
		return doc
	return inner_func

harry_potter_aggregator = concatter()
harry_potter_aggregator("Mr.")
harry_potter_aggregator("and")
harry_potter_aggregator("Mrs.")
harry_potter_aggregator("Dursley")
harry_potter_aggregator("of")
harry_potter_aggregator("number")
harry_potter_aggregator("four,")
harry_potter_aggregator("Privet")

print(harry_potter_aggregator("Drive"))
# Mr. and Mrs. Dursley of number four, Privet Drive
```

Each successive call to `harry_potter_aggregator` mutates that same `doc` variable. When `concatter()` is called, you can think of it as creating a new stateful function that _remembers_ the value of `doc` as it's used.

## NONLOCAL

Python has a keyword called [nonlocal](https://docs.python.org/3/reference/simple_stmts.html#nonlocal) that's required to access variables from an enclosing scope. Most programming languages don't require this keyword, but Python does.