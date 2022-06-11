# Exploring-Find-cmd-in-Linux

There are different type of shell commands, some commands increase our workflow, if we know them well. Find is one of the shell command which is very helpful when we're dealing with large data,files and has to narrow down according to our needs. Basically it makes the enumeration process much faster.


## Usage of Find cmd

Enum the home dir
```markdown
find /home -type f -printf "%f\t%p\t%u\t%g\t%m\n" 2>/dev/null | column -t
```

Find the files in family group
```markdown
find / -type f -group family -ls 2>/dev/null
```

Find all files whose name ends with ".xml"
```markdown
find / -type f -name "*.xml" 2>/dev/null
```

Find all files in the /home directory (recursive) whose name is "user.txt" (case insensitive)
```markdown
find /home -type f -iname user.txt 2>/dev/null
```

Find all directories whose name contains the word "exploits"
```markdown
find / -type d -name "*exploits*" 2>/dev/null
```


## Find cmd With Size
To specify a size, you also need a suffix. c is the suffix for bytes, k for KiB’s, and M for MiB’s


Find all files owned by the user "kittycat"
```markdown
find / -type f -user kittycat
```

Find all files that are exactly 150 bytes in size
```markdown
find / -type f -size 150c
```

Find all files in the /home directory (recursive) with size less than 2 KiB’s and extension ".txt"
```markdown
find/home -type f -size -2k -name "*.txt"
```



## Find cmd with permissions

![OnPaste 20220611-121354](https://user-images.githubusercontent.com/106917304/173176809-0421efac-8662-47d1-bef4-db573398a60e.png)


Find all files that are exactly readable and writeable by the owner, and readable by everyone else (use octal format)
```markdown
find / -type f -perm 644
```

Find all files that are only readable by anyone (use octal format)
```markdown
find / -type f -perm 444
```

Find all files with write permission for the group "others", regardless of any other permissions, with extension ".sh" (use symbolic format)
```markdown
find / -type f -perm -o=w -name "*.sh"
```

Find all files in the /usr/bin directory (recursive) that are owned by root and have at least the SUID permission (use symbolic format)
```markdown
find /usr/bin -type f -user root -perm -u=s
```



## Find cmd for time & days
The words are min and time, for minutes and days, respectively.The prefixes are a, m, and c, and are used to specify when a file was last accessed, modified, or had its status changed.  




Find all files that were not accessed in the last 10 days with extension ".png"
```markdown
find / -type f -atime 10+ -name "*.png"
```

Find all files in the /usr/bin directory (recursive) that have been modified within the last 2 hours
```markdown
find /usr/bin -type f -mmin -120    
```

Find cmd with modify date (eg:14 Feb 2022)
```markdown
find / -type f -name "*.txt" -newermt 2022-02-13 ! -newermt 2022-02-15 2>/dev/null
```

