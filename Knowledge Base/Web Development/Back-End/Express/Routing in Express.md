# Routing in Express

We can use the Express `get()` method to handle GET requests. It takes two arguments:

-   A string with the request, which represents a server path
-   A callback handler which is fired if the server receives that request and the route is a match

```jsx
app.get('/', (req, res) => {
  // the logic for processing the request
});
```

The response object has a `send()` method that sends the response. Information that needs to be sent to the user, e.g. a webpage, is passed as an argument to this method

```jsx
app.get('/', (req, res) => {
  res.send(
        `<html>
        <body>
          <p>Response to the signal from distant space</p>
        </body>
        </html>`
    );
});
```

In addition to sending the response, this method will automatically set the `Content-Type` header as needed according to the type of argument that was passed

```jsx
res.send('some text'); //  Content-Type: text/plain
res.send('<p>some html</p>'); //  Content-Type: text/html
res.send({ some: 'json' }); //  Content-Type: application/json
```

By default, the `send()` method sends a response with a status of 200. This status can also be changed by using the `status()` method

```jsx
app.get('/', (req, res) => {
  res.status(404);
  res.send('<h1>Page not found</h1>');
});
```

```jsx
app.get('/', (req, res) => {
  res.status(404).send('<h1>Page not found</h1>');
});
```

### Request Object

```jsx
const pokemon = {
  grass: {
    stage1: 'Bulbasaur',
    stage2: 'Ivysaur',
    stage3: 'Venusaur'
  },
  fire: {
    stage1: 'Charmander',
    stage2: 'Charmeleon',
    stage3: 'Charizard'
  },
  water: {
    stage1: 'Squirtle',
    stage2: 'Wartotle',
    stage3: 'Blastoise'
  }
};
```

```jsx
GET `${BASE_PATH}/pokemon?type=fire&stage=stage3`; // "Charizard"
```

```jsx
app.get('/pokemon', (req, res) => {
  res.send(pokemon[req.query.type][req.query.stage]);
});
```

### Route parameters

```jsx
app.get('/users/:id/albums/:album/:photo', (req, res) => {
  const { id, album, photo } = req.params;
  /* 
    when requesting "http://localhost:3000/users/123/albums/333/2"
    the request parameters will be written like this:
    {"id":"123","album":"333","photo":"2"}
    we assigned them to the id, album, and photo consts
  */ 

  res.send(`We're on a user's page with the id of ${id}, looking through album #${album}, photo #${photo}`); 
});
```

