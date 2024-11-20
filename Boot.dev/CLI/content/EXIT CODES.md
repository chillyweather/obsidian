# EXIT CODES

[Exit codes](https://en.wikipedia.org/wiki/Exit_status) (sometimes called "return codes" or "status codes") are how programs communicate back whether they ran successfully or not.

`0` is the exit code for success. Any other exit code is an error. 9 times out of 10, if a non-zero exit code is returned (meaning an error) it will be `1`, which is the "catch-all" error code.

Programs that call other programs use error codes to figure out if execution was successful. For example, if the Boot.dev server program exits with a non-zero exit code, we have another program that will automatically restart it and log the error.

In a shell, you can access the exit code of the last program you ran with the question mark (`?`) variable. For example, if you run a program that exits with a non-zero exit code, you can see what it was with the `echo` command:

```bash
ls ~
echo $?
# 0
```

```bash
ls /does/not/exist
echo $?
# 1
```


[[--- INDEX---]]