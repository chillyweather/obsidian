# FIND AND KILL PROCESS

```bash
ps aux | grep "malicious.sh"
#dmitridmitriev   98227   0.0  0.0 408636640   2032 s010  S+    1:48PM   0:00.03 bash ./malicious.sh force
kill 98227
```

Run `ps aux | head -n 1` to see the header row of the ps aux table.

[[--- INDEX---]]