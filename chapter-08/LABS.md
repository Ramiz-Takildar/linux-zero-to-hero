# Chapter 8 Labs

## Lab 8.1: Disk Space
```bash
df -h
du -sh ~
lsblk
```

## Lab 8.2: Mount/Unmount
```bash
cat /proc/mounts
mount | grep ext4
```

## Lab 8.3: LVM Info
```bash
sudo pvs 2>/dev/null || echo "LVM not configured"
sudo vgs 2>/dev/null || echo "LVM not configured"
```
