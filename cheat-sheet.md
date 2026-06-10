# Linux Cheat Sheet

> Quick reference for common Linux commands

---

## 🚀 Quick Navigation

```bash
cd /path          # Change directory
cd ~              # Home directory
cd -              # Previous directory
cd ..             # Parent directory
pwd               # Current directory
ls                # List files
ls -la            # All files, long format
ls -lh            # Human readable
```

---

## 📁 File Operations

```bash
touch file        # Create empty file
cat file          # View file
less file         # Paginated view
head -n 20 file   # First 20 lines
tail -f file      # Follow file
rm file           # Remove file
rm -rf dir        # Force remove directory
cp src dst        # Copy
mv src dst        # Move/rename
mkdir dir         # Create directory
mkdir -p a/b/c    # Create nested
```

---

## 🔍 Finding Things

```bash
find . -name "*.txt"    # Find by name
find . -type d          # Find directories
grep "text" file        # Search in file
grep -r "text" .        # Recursive search
which command           # Command location
whereis command         # Binary and manual
```

---

## 👤 Users & Permissions

```bash
whoami              # Current user
id username         # User info
sudo command        # Run as root
chmod 755 file      # Change permissions
chmod u+x file      # Add execute
chown user file     # Change owner
chown user:grp file # Change owner and group
```

### Permission Numbers

| Number | Permission |
|--------|-----------|
| 7 | rwx (read, write, execute) |
| 6 | rw- |
| 5 | r-x |
| 4 | r-- |
| 0 | --- |

---

## 📦 Package Management

### APT (Debian/Ubuntu)

```bash
sudo apt update          # Update package list
sudo apt upgrade         # Upgrade packages
sudo apt install pkg     # Install package
sudo apt remove pkg      # Remove package
sudo apt purge pkg       # Remove with config
sudo apt search term     # Search
```

### DNF/YUM (RHEL/CentOS)

```bash
sudo dnf install pkg
sudo dnf remove pkg
sudo dnf update
sudo dnf search term
```

---

## ⚙️ Processes

```bash
ps aux              # All processes
top                 # Interactive top
htop                # Enhanced top
kill PID            # Kill process
kill -9 PID         # Force kill
pgrep name          # Find PID
pkill name          # Kill by name
```

---

## 🔄 Services (systemd)

```bash
sudo systemctl status service
sudo systemctl start service
sudo systemctl stop service
sudo systemctl restart service
sudo systemctl enable service
sudo systemctl disable service
```

---

## 🌐 Networking

```bash
ip addr                       # IP addresses
ip route                      # Routing table
ping host                     # Test connectivity
traceroute host               # Trace route
netstat -tlnp                 # Listening ports
ss -tlnp                      # Modern netstat
ssh user@host                 # SSH connect
scp file user@host:/path      # Copy to remote
```

---

## 💾 Storage

```bash
df -h                 # Disk free
du -sh dir            # Directory size
lsblk                 # Block devices
mount dev /mnt        # Mount
umount /mnt           # Unmount
dd if=/dev/zero of=file bs=1M count=100  # Create 100MB file
```

---

## 📝 Text Processing

```bash
cat file |
grep pattern |
sed 's/old/new/g' |
awk '{print $1}' |
sort |
uniq -c |
head -10
```

---

## ⏰ Cron

```bash
crontab -e            # Edit
crontab -l            # List
```

### Time Format

```
* * * * * command
| | | | |
| | | | +--- Day of week (0-7)
| | | +----- Month (1-12)
| | +------- Day (1-31)
| +--------- Hour (0-23)
+----------- Minute (0-59)
```

---

## 📊 System Info

```bash
uname -a              # Kernel info
cat /etc/os-release   # OS version
uptime                # System uptime
free -h               # Memory
cat /proc/cpuinfo     # CPU info
dmesg                 # Kernel messages
lscpu                 # CPU info
lsmem                 # Memory info
```

---

## 🔐 Security

```bash
passwd                # Change password
sudo visudo           # Edit sudoers
last                  # Login history
lastb                 # Failed logins
who                   # Who's logged in
w                     # What they're doing
```

---

## 🛠️ Useful Shortcuts

### Bash Shortcuts

| Key | Action |
|-----|--------|
| Ctrl+C | Cancel command |
| Ctrl+D | Exit/EOF |
| Ctrl+L | Clear screen |
| Ctrl+A | Start of line |
| Ctrl+E | End of line |
| Ctrl+R | Search history |
| Tab | Auto-complete |
| !! | Run last command |
| !n | Run command n from history |

---

<div align="center">

**[⬆ Back to Top](#linux-cheat-sheet)**

</div>
