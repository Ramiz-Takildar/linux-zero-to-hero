# Chapter 10 Labs: Security

## Lab 10.1: Check Security

```bash
# Last logins
last | head -10

# Failed logins
sudo lastb | head -10 2>/dev/null || echo "Need root/logging"

# Current users
who
w

# Check sudo access
sudo -l
```

## Lab 10.2: SELinux Status

```bash
# Check if SELinux is installed
getenforce 2>/dev/null && echo "SELinux installed" || echo "Not installed"

# View context (if installed)
ls -Z /etc/passwd 2>/dev/null
```

## Lab 10.3: Audit

```bash
# Check for SUID files
find /usr/bin -perm -4000 2>/dev/null | head -10

# Check immutable attribute
sudo touch /tmp/testfile
sudo chattr +i /tmp/testfile
lsattr /tmp/testfile
sudo chattr -i /tmp/testfile
rm /tmp/testfile
```
