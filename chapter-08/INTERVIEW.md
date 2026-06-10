# Chapter 8 Interview Questions

## Q1: df vs du?

| df | du |
|----|-----|
| Disk free space | Directory usage |
| Filesystem level | File/directory level |
| Shows available | Shows used |

---

## Q2: What is LVM?

**Answer:**

Logical Volume Manager - abstraction layer between filesystem and physical storage.

**Benefits:**
- Resize volumes dynamically
- Snapshots
- Combine multiple disks
- Easy migration

---

## Q3: fstab purpose?

/etc/fstab defines filesystems to mount at boot.

```
/dev/sda1  /          ext4  defaults  0  0
UUID=xxx   /data      xfs   defaults  0  0
```

---

## Q4: Find largest files/directories?

```bash
du -ah / | sort -rh | head -20
find / -type f -size +100M -exec ls -lh {} \;
```

---

## Q5: Difference between ext4 and xfs?

| ext4 | xfs |
|------|-----|
| Default for most | Large files better |
| Online defrag | No defrag needed |
| Mature | Modern, scalable |
