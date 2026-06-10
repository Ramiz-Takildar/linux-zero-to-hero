# Chapter 3 Labs: Users & Permissions

## Lab 3.1: File Permissions

```bash
# Setup
cd ~
mkdir -p linux-labs/chapter-03
cd linux-labs/chapter-03

touch perms.txt
echo "test content" > perms.txt

# View current permissions
ls -l perms.txt

# Change permissions
chmod 600 perms.txt
ls -l perms.txt

# Add execute for owner
chmod u+x perms.txt
ls -l perms.txt

# Test access
cat perms.txt
./perms.txt  # Won't work (not script)
```

## Lab 3.2: Users and Groups

```bash
# Check current user groups
id
whoami
groups

# View all users
cat /etc/passwd | head -10

# View all groups
cat /etc/group | head -10

# Switch user (if you have password)
su - username

# Or use sudo to run as another user
sudo -u nobody whoami
```

## Lab 3.3: Special Permissions

```bash
# SUID
mkdir special
cd special

touch test.sh
echo "#!/bin/bash" > test.sh
echo "whoami" >> test.sh
chmod u+s test.sh
ls -l test.sh

# Sticky bit
chmod +t .
ls -ld .

cd ~
rm -rf special
```
