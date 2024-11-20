# Web App Security


There are a number of headers responsible for different aspects of security. We’re already familiar with `Content-Security-Policy`, which allows us to restrict the sources of scripts and other resources.

Security headers can be added automatically. There is a `helmet` module to do this. You need to install it, import it, and use it as a middleware:

```jsx
const helmet = require('helmet');

app.use(helmet());

```

`helmet` documentation: [https://www.npmjs.com/package/helmet](https://www.npmjs.com/package/helmet)

### ✅ Check User Data

Validate the input data and replace control characters with entities. If the front-end is inserting them into the site without checking that they are secure, use `escape-html`.

### ✅ Think About Where the Data Is Stored on the Client Side

`LocalStorage` is convenient and simple. It’s perfect for storing data that doesn't need to be hidden. But remember, `localStorage` can be accessed from JavaScript code, and you can't restrict this behavior. Therefore, `httpOnly` cookies are better suited for storing sensitive data.

### ✅ Remember CSRF

If your service relies on cookies being sent automatically by the browser when authorizing requests, implement at least the simplest protection against CSRF. The `SameSite` option will help you with this.

### ✅ Be Prepared for Brute Force and DDOS attacks

To protect yourself from automated requests, use the `express-rate-limit` middleware. It limits the number of requests from one IP address at one time. After installation, it can be imported, configured, and enabled:

```jsx
const express = require('express');
const rateLimit = require('express-rate-limit');

const app = express();

const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // in 15 minutes
  max: 100 // you can make a maximum of 100 requests from one IP
});

// applying the rate-limiter
app.use(limiter);
```

`express-rate-limit` module documentation: [https://www.npmjs.com/package/express-rate-limit](https://www.npmjs.com/package/express-rate-limit).

### ✅ Check the Dependencies

Run the `npm audit` command before sending the project to production. Also set up Security Alert on the platform where you store the code.

### ✅ Never Stop Learning

Security is a huge topic. Big companies hire cybersecurity specialists to protect their services from attacks because the stakes are so high.