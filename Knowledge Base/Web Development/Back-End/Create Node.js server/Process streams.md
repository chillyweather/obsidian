# Streams
```jsx
const http = require('http');

const server = http.createServer((req, res) => {
  let data = '';

  req.on('data', (chunk) => {
    data += chunk.toString();
  });

  req.on('end', () => {
    console.log(JSON.parse(data));
  });
});

server.listen(3000);
```