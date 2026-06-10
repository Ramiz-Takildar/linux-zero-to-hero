# Chapter 6: Shell Scripting

## 📚 Learning Objectives

- Write Bash scripts
- Use variables and data types
- Control flow: if, loops
- Create functions
- Handle strings and arrays

**Estimated Time:** 4 days  
**Labs:** 3

---

## 📝 First Script

### Create and Run

```bash
# Create file
cat > hello.sh << 'EOF'
#!/bin/bash
echo "Hello World"
EOF

# Make executable
chmod +x hello.sh

# Execute
./hello.sh
# or
bash hello.sh
```

### Shebang Line

```bash
#!/bin/bash      # Bash
#!/bin/sh        # POSIX shell
#!/usr/bin/env python3  # Python
```

---

## 📦 Variables

### Basic Variables

```bash
#!/bin/bash

# Assignment (no spaces!)
name="John"
age=30

# Access (use $)
echo $name
echo ${name}      # Safer
echo "Hello $name"
echo 'Hello $name'  # Literal, won't expand

# Readonly
readonly PI=3.14

# Environment variable
export PATH=$PATH:/new/path
```

### Special Variables

| Variable | Meaning |
|----------|---------|
| `$0` | Script name |
| `$1-$9` | Arguments 1-9 |
| `$#` | Number of arguments |
| `$@` | All arguments |
| `$*` | All arguments (as single string) |
| `$$` | Process ID |
| `$?` | Exit status of last command |

---

## 🔀 Control Flow

### If Statements

```bash
#!/bin/bash

# Basic if
if [ condition ]; then
    commands
fi

# If-else
if [ condition ]; then
    commands
else
    commands
fi

# If-elif-else
if [ condition1 ]; then
    commands
elif [ condition2 ]; then
    commands
else
    commands
fi
```

### Test Operators

| Operator | Meaning |
|----------|---------|
| `-eq` | Equal (numbers) |
| `-ne` | Not equal |
| `-lt` | Less than |
| `-gt` | Greater than |
| `-le` | Less or equal |
| `-ge` | Greater or equal |
| `=` | Equal (strings) |
| `!=` | Not equal (strings) |
| `-z` | Empty string |
| `-n` | Non-empty string |
| `-e` | File exists |
| `-f` | Regular file |
| `-d` | Directory |
| `-r` | Readable |
| `-w` | Writable |
| `-x` | Executable |

---

## 🔄 Loops

### For Loop

```bash
# Range
for i in 1 2 3 4 5; do
    echo $i
done

# Sequence
for i in {1..10}; do
    echo $i
done

# With step
for i in {1..10..2}; do
    echo $i
done

# Files
for file in *.txt; do
    echo $file
done

# C-style
for ((i=0; i<10; i++)); do
    echo $i
done
```

### While Loop

```bash
# Basic while
counter=1
while [ $counter -le 5 ]; do
    echo $counter
    ((counter++))
done

# Read file
while read line; do
    echo $line
done < file.txt
```

---

## 📋 Functions

```bash
#!/bin/bash

# Define function
function greet() {
    echo "Hello $1"
}

# Or without 'function' keyword
greet2() {
    echo "Hello $1"
}

# Call function
greet "World"
greet2 "Linux"

# Return value
check_file() {
    if [ -f "$1" ]; then
        return 0
    else
        return 1
    fi
}

# Check return
check_file "/etc/passwd"
echo $?  # 0 = success
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
