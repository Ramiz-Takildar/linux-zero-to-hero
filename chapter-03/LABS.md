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

## Lab 3.4: Sudo Configuration

```bash
# View sudo access
sudo -l

# Check sudo timeout
sudo -k  # Reset timestamp
sudo whoami  # Will ask for password again

# Run command as specific user
sudo -u nobody whoami
sudo -u www-data id

# Edit file with sudo
sudo touch /root/testfile
sudo rm /root/testfile
```

## Lab 3.5: ACL (Access Control Lists)

```bash
# Check if ACL is installed
which getfacl || sudo apt install -y acl

# Create test file
touch acl-test.txt

# View default ACL
getfacl acl-test.txt

# Add ACL for specific user (need another user)
# sudo setfacl -m u:username:rw acl-test.txt

# View updated ACL
# getfacl acl-test.txt

# Remove ACL
# setfacl -b acl-test.txt

# Cleanup
rm acl-test.txt
```

## Lab 3.6: Ownership Transfer

```bash
# Create test files
mkdir ownership-test
cd ownership-test
touch file1 file2 file3

# View current owner
ls -l

# Change owner (need sudo)
sudo chown root file1
ls -l file1

# Change group
sudo chown :users file2
ls -l file2

# Change both
sudo chown root:root file3
ls -l file3

# Recursive change
mkdir subdir
touch subdir/file4
sudo chown -R root: subdir
ls -la subdir

# Cleanup
sudo chown -R $USER: .
cd ~
rm -rf ownership-test
```
