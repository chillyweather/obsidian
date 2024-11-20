![[Pasted image 20211026150241.png]]

![image](https://pictures.s3.yandex.net/resources/S10_10.4_02_01_hooks_local_1596301469.png)

### Destructuring

It's important to note that this hook doesn't "know" which state variable is its responsibility. It simply accepts input values, then returns two things: that same value (with a new value, if you've updated it) and the function that can change this value. On their own, the array elements don't have any names, but with the help of destructuring, we can create two variables and assign them names that are convenient for us.

Thus, the `React.useState()` hook can be used multiple times inside a component to create further pairs for managing individual internal states. Moreover, these state values can contain any type of data, including arrays and objects:

```jsx
const [rating, setRating] = React.useState(0); // -1, 0 or 1
const [isBlocked, setIsBlocked] = React.useState(false); // true or false
const [notes, setNotes] = React.useState(['no notes yet']); // an array of strings
```