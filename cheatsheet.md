## File Viewing & Comparison Commands

### cat — View file contents
| Command | What it does |
|---------|-------------|
| `cat /tmp/hello` | View contents of a file using its full path |
| `cat -n /tmp/hello` | View file with line numbers (-n is a flag/option) |

### head — View beginning of a file
| Command | What it does |
|---------|-------------|
| `head -n1 /tmp/hello` | Show only first 1 line (change 1 to any number) |
| `head -c1 /tmp/hello` | Show only first 1 byte/character |

### tail — View end of a file
| Command | What it does |
|---------|-------------|
| `tail -n1 /tmp/hello` | Show only last 1 line |
| `tail -c1 /tmp/hello` | Show last 1 byte (may show nothing if it's a newline) |
| `tail -c2 /tmp/hello` | Show last 2 bytes (shows last visible character) |

### diff — Compare two files
| Command | What it does |
|---------|-------------|
| `diff file1 file2` | Compare contents of two files |
| `diff -r ~/Desktop ~/Code` | Compare two folders recursively |

### Understanding diff output
```
1c1              → line 1 in file1 needs to CHANGE to match line 1 in file2
< this is file1  → < means this line is from file1
---              → separator between the two files
> this is file2  → > means this line is from file2
```
## File Ownership & Permissions

### chown — Change file/directory ownership

| Command | What it does |
|---------|-------------|
| `ls -l filename` | View file permissions, owner and group |
| `sudo chown root:root filename.txt` | Change owner AND group to root |
| `sudo chown -R root:root new-dir` | Change ownership recursively for entire folder |

**Syntax:** `chown owner:group filename`

---

### chmod — Change file/directory permissions

| Command | What it does |
|---------|-------------|
| `sudo chmod 700 example.txt` | Owner: all permissions. Group: none. Others: none |
| `chmod 755 ~/test-dir` | Owner: all. Group & Others: read + execute only |
| `chmod -R 755 ~/test-dir` | Apply permissions recursively to folder |
| `chmod u+x script.sh` | Add execute permission for owner only |
| `ls -l filename` | View file permissions |
| `ls -ld dirname` | View directory permissions (not its contents) |

---

### Understanding Permission Numbers (chmod)

| Number | Permissions | Calculation |
|--------|------------|-------------|
| 7 | Read + Write + Execute | 4+2+1 = 7 |
| 6 | Read + Write | 4+2+0 = 6 |
| 5 | Read + Execute | 4+0+1 = 5 |
| 4 | Read only | 4+0+0 = 4 |
| 0 | No permissions | 0+0+0 = 0 |

**Example: chmod 700**
```
7 → Owner  → Read + Write + Execute
0 → Group  → No permissions
0 → Others → No permissions
```

**Example: chmod 755**
```
7 → Owner  → Read + Write + Execute
5 → Group  → Read + Execute
5 → Others → Read + Execute
```

---

### Reading Permission Output (ls -l)
```
-rw-rw-r-- 1 root root 0 Jul 29 example.txt
```

| Part | Meaning |
|------|---------|
| `-` | File type: `-` = regular file, `d` = directory, `l` = symlink |
| `rw-` | Owner permissions: read + write, no execute |
| `rw-` | Group permissions: read + write, no execute |
| `r--` | Others permissions: read only |

**Permission letters:**
- `r` = read (4)
- `w` = write (2)  
- `x` = execute (1)
- `-` = permission denied

---

### Symbolic Notation for chmod

| Symbol | Means |
|--------|-------|
| `u` | user/owner |
| `g` | group |
| `o` | others |
| `a` | all (user + group + others) |
| `+` | add permission |
| `-` | remove permission |

**Examples:**
```bash
chmod u+x script.sh    # add execute for owner
chmod g-w file.txt     # remove write from group
chmod a+r file.txt     # add read for everyone
```

---

### Directory Permissions Explained

| Permission | Effect on Directory |
|------------|-------------------|
| `r` | Can list contents using ls |
| `w` | Can create new files inside |
| `x` | Can cd into the directory |

---

### Shell Script Basics
```bash
echo '#!/bin/bash\necho "Hello, World"' > script.sh
```

| Part | Meaning |
|------|---------|
| `#!/bin/bash` | Shebang — tells system to use bash interpreter |
| `echo "Hello, World"` | Prints text to terminal |
| `.sh` | File extension for shell scripts |
| `./script.sh` | Run the script from current directory |
| `chmod u+x script.sh` | Give owner permission to execute it |
