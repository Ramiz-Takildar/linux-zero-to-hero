# Chapter 8 Labs: Storage

## Lab 8.1: Disk Usage

```bash
# Check disk space
df -h

# Check home directory size
du -sh ~

# Find largest directories
du -h ~ | sort -rh | head -10

# List block devices
lsblk
lsblk -f
```

## Lab 8.2: View Mounts

```bash
# Current mounts
mount | head -20

# fstab file
cat /etc/fstab

# Check specific filesystem
df -h /home
```

## Lab 8.3: LVM Info

```bash
# Check if LVM is configured
sudo pvs 2>/dev/null && echo "LVM configured" || echo "No LVM"
sudo vgs 2>/dev/null
sudo lvs 2>/dev/null

# If no output, LVM not set up
```
