# FIND

The `find` command is a powerful tool for finding files and directories by name, not by their contents.

## FIND A FILE BY NAME

Let's say you're looking for a file named `hello.txt` somewhere in your home directory. You can use the `find` command to search for exactly that title:

```bash
find some_directory -name hello.txt
```

## PATTERN SEARCH

The `find` command can also search for files that match a pattern. For example, if you wanted to find all files that end in `.txt`, you could run:

```bash
find some_directory -name "*.txt"
```

The `*` character is a wildcard that matches anything. If you're trying to find filenames that _contain_ a specific word, you can use the `*` character to match the rest of the filename:

```bash
# Find all files that contain the word "chad"
find some_directory -name "*chad*"
```

[[--- INDEX---]]