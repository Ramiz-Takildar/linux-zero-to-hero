# Chapter 1 Interview Questions: Linux Basics

## Basic Concepts

### Q1: What is Linux?

**Answer:**

Linux is an open-source Unix-like operating system kernel created by Linus Torvalds in 1991.

**Key Points:**
- **Kernel:** Core of the operating system
- **Open Source:** Free to use, modify, distribute
- **Unix-like:** Follows Unix philosophy and principles
- **Multi-user:** Multiple users simultaneously
- **Multi-tasking:** Multiple processes concurrently

**Linux vs Linux Distribution:**
- **Linux:** The kernel only
- **Distribution:** Kernel + GNU tools + applications (Ubuntu, CentOS, etc.)

---

### Q2: What are the main components of Linux architecture?

**Answer:**

```
Hardware → Kernel → Libraries → Shell → Applications
```

| Component | Function | Examples |
|-----------|----------|----------|
| **Hardware** | Physical components | CPU, RAM, Disk |
| **Kernel** | Core OS functions | Process, memory management |
| **Libraries** | Shared code | glibc, libssl |
| **Shell** | Command interpreter | Bash, Zsh |
| **Applications** | User programs | Browser, Editor |

---

### Q3: What is the difference between Linux distributions?

**Answer:**

| Distro | Package Manager | Default Init | Best For |
|--------|----------------|--------------|----------|
| **Ubuntu** | APT (apt/deb) | systemd | Beginners, Desktop |
| **Debian** | APT | systemd | Stability, Servers |
| **CentOS/RHEL** | YUM/DNF (rpm) | systemd | Enterprise |
| **Fedora** | DNF | systemd | Latest features |
| **Arch** | Pacman | systemd | Power users |
| **Alpine** | APK | OpenRC | Containers |

**Key Differences:**
- Package management system
- Default software selection
- Release cycle (rolling vs fixed)
- Support and community

---

### Q4: Explain the Linux filesystem hierarchy.

**Answer:**

**Standard Directories (FHS - Filesystem Hierarchy Standard):**

| Directory | Purpose |
|-----------|---------|
| **/** | Root directory |
| **/bin** | Essential user binaries |
| **/sbin** | System binaries |
| **/etc** | Configuration files |
| **/home** | User home directories |
| **/root** | Root user home |
| **/tmp** | Temporary files |
| **/var** | Variable data (logs) |
| **/usr** | User applications |

**Important Files:**
```
/etc/passwd     - User account info
/etc/shadow     - Encrypted passwords
/etc/hosts      - Hostname to IP mapping
/var/log/syslog - System logs
/proc/cpuinfo   - CPU information
```

---

## Commands

### Q5: What is the difference between /bin and /usr/bin?

**Answer:**

| Directory | Purpose | When Available |
|-----------|---------|----------------|
| **/bin** | Essential binaries | Boot time, single-user mode |
| **/usr/bin** | User applications | After /usr is mounted |

**Examples:**
```bash
/bin:    ls, cp, mv, rm, mkdir, cat
/usr/bin: vim, curl, python3, node
```

**Modern Systems:** Often symlinked together

---

### Q6: Difference between cat, less, more, and head/tail?

**Answer:**

| Command | Use Case | Navigation |
|---------|----------|------------|
| **cat** | Small files, concatenate | None (dumps all) |
| **less** | Large files | Up/down, search (/) |
| **more** | Medium files | Forward only |
| **head** | First lines only | None |
| **tail** | Last lines, follow | None (-f for follow) |

**Examples:**
```bash
cat /etc/passwd              # Small file
less /var/log/syslog         # Large file
tail -f /var/log/nginx.log   # Live monitoring
head -50 file.txt            # First 50 lines
```

---

### Q7: What does rm -rf do? Why is it dangerous?

**Answer:**

```bash
rm -rf /path
# -r = recursive (directories)
# -f = force (no prompts)
```

**Dangers:**
- No confirmation prompts
- Immediate deletion
- Cannot be undone easily
- Can destroy system if used on /

**Safe alternatives:**
```bash
rm -i file          # Interactive (prompt)
rm -rfi dir         # Force + interactive
ls target/*         # Verify first, then rm
```

**Infamous:** `rm -rf /` can destroy entire system

---

### Q8: How do you create nested directories in one command?

**Answer:**

```bash
mkdir -p parent/child/grandchild

# -p = --parents
# Creates all necessary parent directories
```

**Without -p:**
```bash
mkdir parent/child
# Error: parent doesn't exist
```

---

## Scenario Questions

### Q9: You accidentally deleted an important file. What do you do?

**Answer:**

1. **Stop writing to disk** (prevent overwriting)
2. **Check backups:**
   ```bash
   ls backup/
   cp backup/file ~/file
   ```
3. **Use recovery tools:**
   ```bash
   # Install testdisk/photorec
   sudo apt install testdisk
   photorec /dev/sda1
   ```
4. **Learn for next time:**
   - Use rm -i (interactive)
   - Create aliases
   - Maintain backups

### Q10: How do you find your current location in the filesystem?

**Answer:**

```bash
pwd
# Print Working Directory

# Option: Show physical path (resolve symlinks)
pwd -P
```

### Q11: How do you switch between two directories quickly?

**Answer:**

```bash
cd /very/long/path/to/project
cd /etc/nginx/sites-available

cd -    # Switch to previous directory
```

---

## Quick Reference

### Directory Shortcuts

| Shortcut | Meaning |
|----------|---------|
| ~ | Home directory |
| . | Current directory |
| .. | Parent directory |
| - | Previous directory |

### File Permissions Preview

```bash
ls -l file.txt
# -rw-r--r-- 1 user group 1234 Jan 1 10:00 file.txt
# |  |  |  |
# |  |  |  +--- Others
# |  |  +------ Group
# |  +--------- Owner
# +------------ Type (- = file, d = dir)
```

---

## Study Tips

- Practice navigating without `cd` (use absolute paths)
- Use `man` pages for detailed info
- Create aliases for common commands
- Understand before memorizing
