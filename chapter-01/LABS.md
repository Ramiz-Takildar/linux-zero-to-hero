# Chapter 1 Labs: Linux Basics

## Lab 1.1: First Login and System Info

**Objective:** Access Linux and explore basic system information.

**Time:** 30 minutes  
**Difficulty:** 🟢 Beginner

### Instructions

#### Step 1: Access Your Linux System

```bash
# If using WSL (Windows)
wsl

# If using SSH
ssh user@your-server-ip

# If using VM - open terminal
```

#### Step 2: Check Current User and Host

```bash
# Who am I?
whoami

# What's my hostname?
hostname

# Full system info
uname -a

# Short version
uname -r
```

#### Step 3: Check Linux Distribution

```bash
# Modern method
cat /etc/os-release

# Output example:
# NAME="Ubuntu"
# VERSION="22.04.1 LTS"
# ID=ubuntu
# ID_LIKE=debian

# Alternative
cat /etc/issue

# For Red Hat systems
cat /etc/redhat-release 2>/dev/null || echo "Not Red Hat"
```

#### Step 4: Check System Resources

```bash
# Memory usage
free -h

# Disk usage
df -h

# CPU info (simplified)
lscpu | head -10

# Uptime
uptime
```

#### Step 5: Date and Time

```bash
# Current date/time
date

# Calendar for current month
cal

# Calendar for year
cal 2024
```

### Verification Checklist

- [ ] Successfully logged into Linux
- [ ] Know current username and hostname
- [ ] Identified Linux distribution
- [ ] Checked system resources
- [ ] Viewed current date/time

---

## Lab 1.2: Navigation Practice

**Objective:** Navigate the Linux filesystem.

**Time:** 30 minutes  
**Difficulty:** 🟢 Beginner

### Instructions

#### Step 1: Current Location

```bash
# Where am I?
pwd

# Output example: /home/username
```

#### Step 2: Explore Root Directory

```bash
# Go to root
cd /

# List contents
ls

# Long listing
ls -l

# All files including hidden
ls -la

# Human readable sizes
ls -lh
```

#### Step 3: Explore System Directories

```bash
# Check /etc
cd /etc
ls | head -20

# Check /var/log
cd /var/log
ls -lh | head -10

# Go back to home
cd ~

# Or use cd with no args
cd
```

#### Step 4: Navigation Shortcuts

```bash
# Go to parent directory
cd ..

# Go to previous directory
cd -

# Go to home
cd ~

# Go to specific user's home
cd ~root   # (need permissions)
```

#### Step 5: Directory Tree View

```bash
# Install tree if not available
sudo apt install tree  # Debian/Ubuntu
sudo yum install tree  # RHEL/CentOS

# View directory structure
tree -L 2 /
tree -L 1 /home
```

### Verification Checklist

- [ ] Used pwd to check location
- [ ] Navigated to /, /etc, /var/log
- [ ] Used cd ~ to go home
- [ ] Used cd .. and cd -

---

## Lab 1.3: File Operations

**Objective:** Create, read, modify, and delete files.

**Time:** 45 minutes  
**Difficulty:** 🟢 Beginner

### Instructions

#### Step 1: Create Lab Directory

```bash
# Create directory structure
cd ~
mkdir -p linux-labs/chapter-01
cd linux-labs/chapter-01

# Verify
pwd
# Should show: /home/username/linux-labs/chapter-01
```

#### Step 2: Create Files

```bash
# Create empty files
touch file1.txt
touch file2.txt file3.txt

# Create file with content
echo "Hello, Linux!" > hello.txt

# Alternative
cat > manual.txt << 'EOF'
This is a manual file.
It has multiple lines.
EOF

# List files
ls -lh
```

#### Step 3: Read Files

```bash
# Display content
cat hello.txt

# View with line numbers
cat -n manual.txt

# View first few lines
head manual.txt

# View last few lines
tail manual.txt

# Interactive viewer (q to quit)
less /etc/passwd
```

#### Step 4: Modify Files

```bash
# Append to file
echo "New line" >> hello.txt

# Overwrite file
echo "Replaced content" > file1.txt

# View history of a file (needs git - we'll cover later)
# For now just view
cat hello.txt
```

#### Step 5: Copy and Move

```bash
# Copy file
cp hello.txt hello-backup.txt
ls

# Copy to directory
mkdir backup
cp *.txt backup/
ls backup/

# Move/rename file
mv file1.txt renamed.txt
ls

# Move to directory
mv file2.txt backup/
ls backup/
```

#### Step 6: Remove Files

```bash
# Remove single file
rm file3.txt

# Remove with confirmation
rm -i hello-backup.txt

# Remove directory with contents
rm -r backup

# Create and force remove
tempfile temp.txt
rm -f temp.txt  # No confirmation
```

#### Step 7: Create Directories

```bash
# Create single directory
mkdir testdir

# Create nested directories
mkdir -p very/deep/nested/dir

# Verify
tree very/

# Remove nested directories
rm -r very

# Clean up
cd ~
rm -rf linux-labs
```

### Verification Checklist

- [ ] Created directories with mkdir
- [ ] Created files with touch and echo
- [ ] Read files with cat, head, tail, less
- [ ] Copied files with cp
- [ ] Moved/renamed with mv
- [ ] Removed files with rm
- [ ] Used mkdir -p for nested dirs

---

## Summary

You should now be able to:
- ✅ Log into a Linux system
- ✅ Use pwd, cd, ls for navigation
- ✅ Create files with touch and echo
- ✅ View files with cat, less, head, tail
- ✅ Copy, move, and delete files
- ✅ Create and remove directories

---

## Next Steps

1. Review any labs you struggled with
2. Answer the [Interview Questions](./INTERVIEW.md)
3. Update your [CHECKLIST.md](../CHECKLIST.md)
4. Move to [Chapter 2](../chapter-02/)
