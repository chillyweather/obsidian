One of the most beautiful things about the shell is that you can [pipe](https://en.wikipedia.org/wiki/Pipeline_%28Unix%29) the output of one program into the input of another program. With this one simple concept, you can run incredibly powerful automation tasks.

## PIPE

The pipe operator is `|`. It's the character that looks like a vertical line. It's usually on the same key as the backslash (`\`) above the enter key. The pipe operator takes the stdout of the program on the left and "pipes" it into the stdin of the program on the right.

```bash
echo "Have you heard the tragedy of Darth Plagueis the Wise?" | wc -w
# 10
```

In the example above, the `echo` command sends "Have you heard the tragedy of Darth Plagueis the Wise?" to stdout.

However, instead of that text being sent to your terminal, the pipe operator pipes it into the `wc` (word count) command. The `wc` command counts the number of words in the input it receives. The `-w` flag tells `wc` to only count words.

This only works because the `wc` command, like most shell commands, can optionally read from stdin instead of a filepath.

```bash
grep -R "Bob" transactions --exclude-dir="backups" | wc -l
#3973
```

↑ Use the `grep` command to find all lines in all of the transactions that include the word "Bob". You'll want to include all of the files in the `worldbanc/private/transactions` directory, but _not_ the files in the `backups` directory.

Then, pipe the output of that command into the `wc -l` command to count the number of lines.

[[--- INDEX---]]