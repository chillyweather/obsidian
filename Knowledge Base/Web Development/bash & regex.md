# bash & regex

#### Aliases
```bash
alias ls='ls -F'
```

#### Misc

`cat` - read file (concatenate too)

`cp -r`  - recursive copy


`$ mkdir text{1..5}`
```bash
ddzmi@cwLaptop MINGW64 ~/Documents/test
$ touch {1,2,3}{a,b,c}.txt

ddzmi@cwLaptop MINGW64 ~/Documents/test
$ ls
1a.txt  1b.txt  1c.txt  2a.txt  2b.txt  2c.txt  3a.txt  3b.txt  3c.txt  a/
```

`wc` - word count

`head` - print 10 first lines of a file
`head -n7` - 7 lines 

`ls > 2a.txt` save output to file

`echo soon more >> 2a.txt` append to file

`<` send to the standard input

#### pipes

`|` connects outputs to inputs

 `curl` transfer from url !!!
 
 `cal` calendar
 
 `date` date  
 
 `fold` shorten lines of text
 
 `awk`
 
 ### Shell scripts
 `vi logger`
 ```vi
 echo `date +'%F %T'` $@ >> `date +%F`.log
 ```
 `chmod +x logger`
 `./logger testing test of a tested`
 
 ##### Add script to PATH
 `sudo cp logger /usr/local/bin/logger`