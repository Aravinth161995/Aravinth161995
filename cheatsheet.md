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
