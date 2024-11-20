# Response Caching

By default, `GET` requests are cached by browsers. However, `POST` requests aren't cached by default, and `PUT`, `PATCH`, and `DELETE` requests aren't cached at all.

**Special headers** for `GET` and `POST` requests are responsible for the caching logic.

- **Expires **
Data may have a limited period of validity. The Expires header allows us to indicate a time frame over which the cached data will remain valid. When this time ends, the data will again be requested from the server, instead of being taken from the cache. The cache itself will then be updated
`Expires: Fri, 20 May 2016 19:20:49 IST`
- **Cache-Control**
In this header, we indicate a directive for handling cached data
```jsx
// cache control

Cache-Control: only-if-cached // If the response is in the cache, it will be returned from there. If not, the browser will respond with a 504 error
Cache-Control: no-cache // The browser makes a conditional validation request to the server. If there are changes on the server, the cache will be updated.

// max-age management

Cache-Control: max-age=30000 // the maximum time in seconds during which a resource is considered relevant

// cache update management

Cache-Control: must-revalidate // if the cache has expired, a request will be sent to check the data in the cache

// other

Cache-Control: no-store // cache disabled
```

  Proxy control
```jsx
Cache-Control: private // data can only be cached on the client side
Cache-Control: public // data can be cached on proxy servers

Cache-Control: proxy-revalidate // before using data from the proxy server cache, you should check if it's relevant

Cache-Control: no-transform // proxies can't apply any changes to the resource. other settings — private, public and proxy-revalidate — don't impose such restrictions
```
```jsx
Cache-Control: max-age=30000, must-revalidate
```
- **ETag**
An algorithm analyzes the cache and creates a string called a [hash](https://practicum.yandex.com/trainer/web-practicum100/lesson/37d53dd9-e7cf-42ee-ac56-b4f17bf615c6) (we mentioned it back in the chapter on Git). This string will be unique for any dataset. We can simply store this string in the cache and then pass it for validation. Overall, this is a lot more efficient.

A hash can be written to the `ETag` header. If the response body changes, so does the hash:
```jsx
ETag: "abcd1234567n34jv"
```
- **Last-Modified**
```jsx
Last-Modified: Fri, 10 May 2016 09:17:49 IST
```

### Express cache headers

By default, express works as follows:

-   Creates an `ETag` response header that is sent in every server response. Thus, every response is cached.
-   The browser remembers the value of the header and at the next `GET` request it sends the `ETag` inside another header — `If-None-Match`.
-   If the value of the `If-None-Match` header matches some cache on the server, the response will be under the `304` Not Modified status code. As a result, the browser will take the response value from its cache.

`POST` requests aren't cached by default. In fact, `POST` requests are rarely cached. But still, it's possible to do this by manually setting the caching headers.

## Example
```jsx
//app.js
const path = require('path');
const express = require('express');
const {setNoCacheHeaders} = require('./middleware')

const { PORT = 3000, BASE_PATH } = process.env;
const app = express();



app.use(setNoCacheHeaders)
app.use(express.static(path.join(__dirname, 'public')));


app.listen(PORT, () => {
  console.log('Link to the server');
  console.log(BASE_PATH);
});

```

```jsx
//middleware.js
const setNoCacheHeaders = (req, res, next) => {
  res.header('Cache-Control', 'no-store');
  next();
};

module.exports = {
  setNoCacheHeaders
};
```