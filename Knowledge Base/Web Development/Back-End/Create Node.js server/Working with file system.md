# Working with file system

### readfile()

This function works asynchronously and takes three arguments: the name of the file that we want to read, an options object (optional), and a callback. In the callback, we need to describe what should be done with the data.

The callback has two parameters. Normally, the first parameter of a Node.js callback is an `err` parameter, which is used to handle potential errors. Second, we have the `data` parameter, which represents the contents of the file.

```jsx
const fs = require('fs');

fs.readFile('data.json', (err, data) => {
  if (err) {
    console.log(err);
    return;
  }

  console.log('data: ', data.toString('utf8'));
});
```

```jsx
const fs = require('fs');

fs.readFile('data.json', { encoding: 'utf8' }, (err, data) => { // the options object is passed as the second argument. It contains the encoding property, in which we specify the character encoding to use 
  if (err) {
    console.log(err);
    return;
  }

  console.log('data: ', data); // since the data comes as a string, we don't need to call the toString() method here 
});
 
```

### readdir() - read all files in directory
The first argument of this method is the path to the directory. The second one is a callback, which describes what should be done with the data returned.

The callback also has two parameters — an error parameter (`err`) and an array of the file names

```jsx
const fs = require('fs');

fs.readdir('.', (err, files) => {
  if (err) {
    console.log(err);
    return;
  }

  console.log('data: ', files);
});
```

### fs.mkdir()
It takes two arguments: the name of the new folder, and a callback with a single argument, i.e. the error object. When passing the first argument, we can specify the path to this new file along with its name:

```jsx
const fs = require('fs');

fs.mkdir('incomingData/data', (err) => {
  if (err) console.log(err);
});
```

### fs.writeFile()
It has three parameters:

-   The file to which we want to write data
-   Data in the form of a string
-   A callback for error processing
```jsx
const fs = require('fs');

fs.writeFile('data.json', JSON.stringify([1, 2, 3]), (err) => {
  if (err) console.log(err);
});
```

### fs.unlink() - delete file
```jsx
const fs = require('fs');

fs.unlink('data.json', (err) => {
  if (err) {
    console.log(err);
    return;
  }

  console.log('The file was deleted!'); 
});
```

-------
-------
## Using Promises when Working with Files
```jsx
const fsPromises = require('fs').promises;

fsPromises.readFile('data.json', { encoding: 'utf8' })
  .then((data) => {
    console.log(data);
  })
  .catch(err => {
    console.log(err);
  });
```
-------
-------
Every module contains the `__filename` and `__dirname` variables, which store the module's file path and directory path, respectively.
```jsx
// app.js

console.log(__filename); // /usr/local/project/app.js
console.log(__dirname); // /usr/local/project
```
## Path
The `path` module provides various methods for working with file and directory paths. One of these methods is the `join()` method, which joins the specified path segments together and returns what's referred to as a normalized path. This method accounts for the operating system being used, so we avoid any problems with slashes
```jsx
// read-file.js

const fs = require('fs');
const path = require('path');

module.exports.readFile = () => {
  const filepath = path.join(__dirname, 'file.txt'); // joining the path segments to create an absolute path
  const file = fs.readFile(filepath, { encoding: 'utf8' }, (err, data) => {
    console.log(data);
  }); 
};
```
```jsx
const fs = require('fs');
const path = require('path');

// the path.normalize() method normalizes the specified path
// and resolves '..' and '.' segments
path.normalize('/foo/bar//baz/asdf/quux/..'); // /foo/bar/baz/asdf

// the path.dirname() method returns the directory name of the given path
path.dirname(require.main.filename); // /usr/local/my-project

// the path.extname() method returns the extension of a file path
path.extname('app.js'); // .js
```