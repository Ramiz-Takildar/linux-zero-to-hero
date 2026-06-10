# Chapter 2 Labs

## Lab 2.1: Copy and Move
```bash
cp /etc/hosts ~/hosts.backup
mv ~/hosts.backup ~/hosts.bak
```

## Lab 2.2: Find
```bash
find /var/log -name "*.log"
find . -type d
```

## Lab 2.3: Links
```bash
touch original
ln original hardlink
ln -s original symlink
ls -li
```
