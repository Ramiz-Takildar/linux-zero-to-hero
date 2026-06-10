# Chapter 6 Interview Questions

## Q1: Shebang line purpose?

**Answer:**

Tells system which interpreter to use for the script.

```bash
#!/bin/bash     # Use Bash
#!/bin/sh       # Use POSIX shell
#!/usr/bin/env python3  # Find Python 3
```

---

## Q2: Difference between $* and $@?

| $* | $@ |
|----|-----|
| All args as single string | Each arg separately |
| "$*" = "arg1 arg2 arg3" | "$@" = "arg1" "arg2" "arg3" |

**Use $@** for most cases

---

## Q3: Check if command succeeded?

```bash
if command; then
    echo "Success"
else
    echo "Failed"
fi

# Or check exit code
command
echo $?   # 0 = success
```

---

## Q4: Difference between = and -eq?

| = | -eq |
|---|-----|
| String comparison | Numeric comparison |
| "10" = "010" is false | 10 -eq 010 is true |

---

## Q5: Prevent word splitting in variables?

```bash
name="John Doe"
echo "$name"    # Safe: "John Doe"
echo $name      # Unsafe: splits to "John" "Doe"
```

**Always quote variables!**
