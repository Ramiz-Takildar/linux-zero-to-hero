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

## Lab 8.4: Working with Filesystems

```bash
# View filesystem types
df -Th

# Check inode usage
df -i

# Find files by size
find ~ -type f -size +10M -ls 2>/dev/null

# Find empty directories
find ~ -type d -empty 2>/dev/null

# Find empty files
find ~ -type f -empty 2>/dev/null

# Check disk usage by file type
du -h ~ | sort -rh | head -20
```

## Lab 8.5: Mount Operations

```bash
# View kernel mount info
cat /proc/mounts | head -10

# View mount options
mount | grep ext4 | head -5

# Check if directory is mount point
mountpoint ~/linux-labs && echo "Is mount point" || echo "Not mount point"

# View filesystems supported by kernel
cat /proc/filesystems

# Check UUID of devices
sudo blkid | head -10
```

## Lab 8.6: Swap Management

```bash
# View swap usage
free -h | grep Swap
swapon -s

# View swap file/partition
cat /proc/swaps

# Check if using swap
vmstat 1 5 | tail -4

dmesg | grep -i swap | tail -5
```

## Lab 8.7: Disk I/O Monitoring

```bash
# Install iostat if needed
which iostat || sudo apt install -y sysstat

# View disk I/O statistics (run twice with delay)
iostat -x 1 3

# View per-partition stats
iostat -p

# Alternative: iotop (if installed)
# sudo iotop -o -b -n 5
```
