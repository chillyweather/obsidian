# Streams for reading and writing files
```jsx
const fs = require('fs');

const reader = fs.createReadStream('./in.txt', { encoding: 'utf8' });
const writer = fs.createWriteStream('./out.txt', { encoding: 'utf8' });

reader.on('data', (data) => {
  writer.write(data);
});

reader.on('end', (data) => {
  writer.end();
});

// add an event listener to the error event
reader.on('error', (err) => {
  console.log(err);
});
```

### The `pipe()` method for working with streams
We can make our code noticeably shorter with the help of a special method that "pipes" our stream together: `pipe()`. This avoids the need to close streams or handle errors as all the necessary logic is already built into the implementation of the `pipe()` method.

```jsx
const fs = require('fs');

const reader = fs.createReadStream('./in.txt', { encoding: 'utf8' });
const writer = fs.createWriteStream('./out.txt', { encoding: 'utf8' });

reader.pipe(writer);
```

```jsx
const http = require('http');
const fs = require('fs');

const server = http.createServer(function (req, res) {
  req.pipe(fs.createWriteStream(`./out-${Math.random()}.txt`));
});

server.listen(3000);
```