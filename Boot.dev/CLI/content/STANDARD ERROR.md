# STANDARD ERROR

["Standard Error"](https://en.wikipedia.org/wiki/Standard_streams#Standard_error_%28stderr%29), usually called "stderr", is the same thing as standard output, but for error messages. It's a stream completely separate from stdout so that you can redirect it to a different place if need be, but by default, it prints to your terminal just like stdout.

## REDIRECTING STREAMS

You can redirect stdout and stderr to different places using the `>` and `2>` operators. `>` redirects stdout, and `2>` redirects stderr.

### REDIRECT STDOUT TO A FILE

```bash
echo "Hello world" > hello.txt
cat hello.txt
# Hello world
```

### REDIRECT STDERR TO A FILE

```bash
cat doesnotexist.txt 2> error.txt
cat error.txt
# cat: doesnotexist.txt: No such file or directory
```

[[--- INDEX---]]