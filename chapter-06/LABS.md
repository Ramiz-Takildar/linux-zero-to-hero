# Chapter 6 Labs

## Lab 6.1: First Script
```bash
cat > hello.sh << 'EOF'
#!/bin/bash
echo "Hello $USER"
date
EOF
chmod +x hello.sh
./hello.sh
```

## Lab 6.2: Loop Script
```bash
cat > count.sh << 'EOF'
#!/bin/bash
for i in {1..5}; do
    echo "Count: $i"
done
EOF
chmod +x count.sh
./count.sh
```

## Lab 6.3: If Statement
```bash
cat > check.sh << 'EOF'
#!/bin/bash
if [ -f /etc/passwd ]; then
    echo "Passwd exists"
fi
EOF
chmod +x check.sh
./check.sh
```
