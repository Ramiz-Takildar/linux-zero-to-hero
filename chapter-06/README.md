# Chapter 6: Shell & Scripting

## 📚 Learning Objectives

- Bash scripting
- Variables, loops, functions

**Estimated Time:** 4 days  
**Labs:** 3

---

## 📝 Basic Script

```bash
#!/bin/bash
# My first script

echo "Hello World"
name="Linux"
echo "Hello $name"
```

## 🔧 Control Structures

```bash
# If statement
if [ -f file.txt ]; then
    echo "File exists"
fi

# For loop
for i in 1 2 3; do
    echo $i
done

# While loop
while [ condition ]; do
    # commands
done

# Case statement
case $var in
    pattern1) commands ;;
    pattern2) commands ;;
esac
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
