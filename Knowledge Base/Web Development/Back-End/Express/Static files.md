# Static files
access to root directory
 ```jsx
 app.use(express.static(__dirname)); 
// here we made all files on the server now available to the user 
 ```
 
 public folder access
 ```jsx
app.use(express.static(__dirname + '/public'));
// now the client only has access to public files
 ```
 
 