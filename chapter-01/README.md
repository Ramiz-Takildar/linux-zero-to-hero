# Chapter 1: Linux Basics & Installation

## 📚 Learning Objectives

By the end of this chapter, you will:
- Understand what Linux is and its history
- Know different Linux distributions
- Navigate the Linux filesystem
- Use basic Linux commands
- Install a Linux system

**Prerequisites:** Basic computer knowledge  
**Estimated Time:** 2 days  
**Labs:** 3 hands-on exercises

---

## 🐧 What is Linux?

Linux is an open-source Unix-like operating system kernel created by Linus Torvalds in 1991.

### Linux vs Other Operating Systems

| Feature | Windows | macOS | Linux |
|---------|---------|-------|-------|
| **Cost** | Paid | Free with hardware | Free |
| **Open Source** | No | Partial | Yes |
| **Customizable** | Limited | Medium | High |
| **Security** | Good | Good | Excellent |
| **Servers** | Common | Rare | Dominant |

### Why Learn Linux?

- **95% of cloud servers** run Linux
- **90% of public clouds** use Linux
- **Android** is based on Linux
- **DevOps, Cloud, SRE** roles require Linux skills

---

## 🏗️ Linux Architecture

```
┌─────────────────────────────────────┐
│  Applications (Browser, Editor)     │
├─────────────────────────────────────┤
│  Shell (Bash, Zsh)                  │
├─────────────────────────────────────┤
│  System Libraries (glibc)           │
├─────────────────────────────────────┤
│  Linux Kernel                       │
│  - Process management               │
│  - Memory management                │
│  - Device drivers                   │
│  - File system                      │
├─────────────────────────────────────┤
│  Hardware (CPU, Memory, Disk)       │
└─────────────────────────────────────┘
```

---

## 📦 Linux Distributions

### Popular Distros

| Distro | Package Manager | Best For |
|--------|----------------|----------|
| **Ubuntu** | APT | Beginners, desktops |
| **Debian** | APT | Servers, stability |
| **CentOS/RHEL** | YUM/DNF | Enterprise servers |
| **Fedora** | DNF | Latest features |
| **Arch** | Pacman | Power users |
| **Alpine** | APK | Containers |

### Choosing a Distro

- **Beginner:** Ubuntu, Linux Mint
- **Server:** Debian, CentOS, Ubuntu Server
- **Enterprise:** RHEL, SUSE
- **Learning:** Any (Ubuntu recommended)

---

## 📁 Linux Filesystem Hierarchy

```
/                           # Root directory
├── /bin                    # Essential binaries (ls, cp, mv)
├── /boot                   # Boot loader files
├── /dev                    # Device files
├── /etc                    # Configuration files
├── /home                   # User home directories
│   ├── /home/alice
│   └── /home/bob
├── /lib                    # Shared libraries
├── /media                  # Mount points for removable media
├── /mnt                    # Temporary mount points
├── /opt                    # Optional software
├── /proc                   # Process information (virtual)
├── /root                   # Root user's home
├── /run                    # Runtime variable data
├── /sbin                   # System binaries (root only)
├── /tmp                    # Temporary files
├── /usr                    # User programs
│   ├── /usr/bin            # User binaries
│   ├── /usr/lib            # Libraries
│   └── /usr/local          # Locally installed software
├── /var                    # Variable data
│   ├── /var/log            # Log files
│   ├── /var/spool          # Spool files
│   └── /var/www            # Web server files
```

### Key Directories Explained

| Directory | Purpose |
|-----------|---------|
| **/bin** | Essential commands for all users |
| **/sbin** | System administration commands |
| **/etc** | System-wide configuration |
| **/home** | User personal directories |
| **/tmp** | Temporary files (cleared on reboot) |
| **/var** | Variable data (logs, databases) |
| **/usr** | User applications |

---

## ⌨️ Basic Commands

### Navigation

```bash
pwd                         # Print working directory
cd /home/user               # Change directory
cd ~                        # Go to home directory
cd ..                       # Go up one directory
cd -                        # Go to previous directory
ls                          # List files
ls -l                       # Long format listing
ls -la                      # List all (including hidden)
ls -lh                      # Human readable sizes
```

### File Operations

```bash
touch file.txt              # Create empty file
cat file.txt                # Display file content
less file.txt               # View with pagination
head -20 file.txt           # First 20 lines
tail -20 file.txt           # Last 20 lines
tail -f /var/log/syslog     # Follow file changes
mkdir mydir                 # Create directory
mkdir -p parent/child       # Create nested directories
rm file.txt                 # Remove file
rm -r mydir                 # Remove directory
rm -rf mydir                # Force remove (DANGEROUS)
cp file1 file2              # Copy file
cp -r dir1 dir2             # Copy directory
mv file1 file2              # Move or rename file
```

### System Info

```bash
whoami                      # Current user
hostname                    # System hostname
uname -a                    # Kernel information
cat /etc/os-release         # OS version
uptime                      # System uptime
man command                 # Manual page
command --help              # Command help
```

---

## 🛠️ Installation Methods

### 1. Virtual Machine (Recommended for Learning)

```bash
# Using VirtualBox
# 1. Download Ubuntu ISO
# 2. Create VM: 2GB RAM, 20GB disk
# 3. Install Ubuntu
# 4. Start learning
```

### 2. Windows Subsystem for Linux (WSL)

```powershell
# Windows 10/11
wsl --install

# Then access via:
# wsl or Ubuntu from Start menu
```

### 3. Cloud VPS (Free Tiers)

- AWS EC2 Free Tier (750 hours/month)
- Google Cloud Free Tier
- Oracle Cloud Free Tier
- DigitalOcean ($100 credit)

### 4. Docker

```bash
docker run -it ubuntu:22.04 bash
```

---

## 🎨 Best Practices

### Command Line Tips

```bash
# Use tab completion
cat /et<TAB>/os<TAB>    # Auto-completes

# Use arrow keys
# Up: Previous command
# Down: Next command
# Ctrl+R: Search history

# Clear screen
Ctrl+L    # or type "clear"

# Cancel command
Ctrl+C
```

### File Naming

- Avoid spaces in filenames (use underscores)
- Case-sensitive: File.txt ≠ file.txt
- Hidden files start with dot: .bashrc

---

## 📖 Key Takeaways

1. **Linux is everywhere** - servers, cloud, mobile, IoT
2. **Distributions** package the kernel with tools
3. **Filesystem hierarchy** is standardized
4. **Commands are case-sensitive**
5. **/etc** for config, **/home** for users, **/var** for logs

---

## 🔗 Next Steps

1. Complete [Lab 1.1](./LABS.md) - First Login
2. Complete [Lab 1.2](./LABS.md) - Navigation
3. Complete [Lab 1.3](./LABS.md) - File Operations
4. Review [Interview Questions](./INTERVIEW.md)
5. Update [CHECKLIST.md](../CHECKLIST.md)

**Next Chapter:** [Chapter 2: Files & Directories](../chapter-02/)
