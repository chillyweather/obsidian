
### BASIC USAGE

The most basic usage of `grep` is to search for a string in a file. For example, if we wanted to search for the word "hello" in the file `hello.txt`, we could run:

```bash
grep "hello" hello.txt
```

# GREP MULTIPLE FILES

You can also search multiple files at once. For example, if we wanted to search for the word "hello" in `hello.txt` and `hello2.txt`, we could run:

```bash
grep "hello" hello.txt hello2.txt
```

### RECURSIVE SEARCH

You can also search an entire directory, including all subdirectories. For example, if we wanted to search for the word "hello" in the current directory and all subdirectories, we could run:

```bash
grep -r "hello" .
```

[[--- INDEX---]]