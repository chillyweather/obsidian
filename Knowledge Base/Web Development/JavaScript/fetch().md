
```js
fetch("https://example.com/users", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    username: "arthur"
  })
});
```

```js
fetch("https://example.com")
  .then((res) => {
    console.log(res); // if everything is ok, we receive the response
  })
  .catch((err) => {
    console.log("Error. The request failed");
  });
```


```js
```js
fetch('https://jsonplaceholder.typicode.com/posts', {
  method: 'POST',
  body: JSON.stringify({
    title: 'foo',
    body: 'bar',
    userId: 1,
  }),
  headers: {
    'Content-type': 'application/json; charset=UTF-8',
  },
})
  .then((response) => response.json())
  .then((json) => console.log(json));
```
```