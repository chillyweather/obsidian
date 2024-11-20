# Testing HTTP Requests

 [SuperTest](https://github.com/visionmedia/supertest#readme) library, which provides convenient tools for creating such tests.
 
 SuperTest works as follows: start testing → connect to the server → run tests → disconnect from the server → finish tests. The main takeaway here is that SuperTest takes charge of connecting to and from the server.
 
 When running tests, `process.env.NODE_ENV` is automatically set to `"test"` by the Jest runner. So, we can just check for that and only start listening to port 3000 when not running in test mode:
 
 ```jsx
 if (process.env.NODE_ENV !== "test") {
  app.listen(PORT, () => {
    console.log(`App listening on port ${PORT}`);
  });
}
 ```
 
 ## Installing SuperTest

Run the command `npm install --save-dev supertest`.

```jsx
// package.json
"scripts": {
  "start": "node app.js"
}
```

Create an `endpoint.test.js` file for our tests. Connect the library to this file:
```jsx
// endpoint.test.js
const supertest = require('supertest');
const app = require('./app.js');
```

The `supertest` variable contains a function. Pass your app to it as follows:

```jsx
const request = supertest(app);
```

All done! Now we can access the library's methods through the `request` object. All methods of this object will return promises that need to be processed asynchronously.

### Checking Request Sending

For each type of request, there is a method with the same name: `get()`, `post()`, `delete()`, `put()`, and `patch()`. For each of these methods, we pass the URL of the request we want to check as an argument:

```jsx
describe('Endpoints respond to requests', () => {
  it('Returns data and status 200 on request to "/"', () => {
    return request.get('/').then((response) => {
            expect(response.status).toBe(200);
            expect(response.text).toBe('Hello, world!');
        });
  });
});
```

When testing promises, return them by writing `return` before `request.get()`. This will automatically make Jest wait for the promise to resolve or report an error if it's rejected.

### Configuring Requests

In addition to URLs, requests have attributes. Some of these attributes can contain files. Let's have a look at the corresponding methods.

`set()` sets the attributes. It has two parameters: the name of the attribute and its value:

```jsx
.set('Cookie', ['token=u1a90aw7812689adukqyw61;'])
```

`send()` sets the request body. The method name may be confusing, but we can easily remember the difference: the `get()`, `post()`, `delete()`, `put()`, and `patch()` methods are used to send requests, while `send()` allows us to add data to the request body:

```jsx
.send({ name: 'Mr Pink' })
```

`query()` allows us to configure a `GET` request, which doesn't have a body, only a URL. To add data to this URL, pass the data to the `query()` method inside an object, like this:

```jsx
.query({ per_page: '50', offset: '20' })
```

`attach()` is used to attach a file to the request. The first parameter is the file name, the second is the relative path to it:

```jsx
.attach('avatar', 'test/fixtures/avatar.jpg')
```

Notice the `fixtures` directory. This is a common way to name a directory containing all the necessary data for testing, such as picture, audio, and video files.
