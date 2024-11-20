
## Array and stuff

- read about Iterators and Generators
	- generators yield something on every request, like next value from some function or in the list
	- 📖 **ask ChatGpt for deeper understanding**
- finding:
	- find
	- findIndex
	- findLast
	- findLastIndex
- array.at(x):
	- as using [x] but can use negative numbers for position
- change by copy:
	- array.toReversed();
	- array.toSorted();
	- array.toSpliced();
	- array.with(2,10) - creates new array with value at index 2 set to 10;

## Async & Promises

#### Promise.allSettled()

when all promises in array are resolved

```js
const promises = [
  fetch("");
  fetch("");
  fetch("");
  ]; 
  
Promise.allSettled(promises).then(res => console.log(res)
```

#### Promise.any()

same but when first (any one) resolved

### Misc
#### Proper Tail Call
- Faster recursive function using accumulator value 
  📖 **read more**
#### Tagged templates
- 📖 **read more**
