# CHMOD

```bash
chmod -R u=rwx,g=,o= DIRECTORY
```

In the command above, `u` means "user" (aka "owner"), `g` means "group", and `o` means "others". The `=` means "set the permissions to the following", and the `rwx` means "read, write and execute". The `g=` and `o=` mean "set group and other permissions to nothing". The `-R` means "recursively", which means "do this to all of the contents of the directory as well".

### Remove execution
```bash
chmod -x genids.sh
```

### Add execution
```bash
chmod +x genids.sh
```

[[--- INDEX---]]