# Chapter 6 Labs: Shell Scripting

## Lab 6.1: First Script

```bash
cd ~
mkdir -p linux-labs/chapter-06
cd linux-labs/chapter-06

# Create hello script
cat > hello.sh << 'EOF'
#!/bin/bash
echo "Hello, $USER!"
echo "Today is $(date)"
echo "Current directory: $(pwd)"
EOF

chmod +x hello.sh
./hello.sh
```

## Lab 6.2: Variables and Arguments

```bash
# Create script with arguments
cat > args.sh << 'EOF'
#!/bin/bash
echo "Script name: $0"
echo "First argument: $1"
echo "Second argument: $2"
echo "All arguments: $@"
echo "Number of arguments: $#"
EOF

chmod +x args.sh
./args.sh apple banana cherry
```

## Lab 6.3: If Statement

```bash
# File checker
cat > filecheck.sh << 'EOF'
#!/bin/bash
if [ -f "$1" ]; then
    echo "File exists"
elif [ -d "$1" ]; then
    echo "Directory exists"
else
    echo "Not found"
fi
EOF

chmod +x filecheck.sh
./filecheck.sh /etc/passwd
./filecheck.sh /tmp
./filecheck.sh /notreal
```

## Lab 6.4: For Loop

```bash
# Create numbers script
cat > numbers.sh << 'EOF'
#!/bin/bash
for i in {1..5}; do
    echo "Number: $i"
done
EOF

chmod +x numbers.sh
./numbers.sh
```
