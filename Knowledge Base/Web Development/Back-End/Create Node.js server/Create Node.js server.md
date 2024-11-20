# Create Node.js server



```jsx
const http = require('http');
const server = http.createServer((req, res) => {
    res.writeHead(200, {
        'Content-Type': 'text/html; charset=utf8'
    });
    // we can also pass data to the end() method
    res.end('<h1>Hello, World!</h1>', 'utf8');
});

const { PORT=3000 } = process.env;

server.listen(PORT); 
```

