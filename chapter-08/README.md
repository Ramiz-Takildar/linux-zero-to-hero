# Chapter 8: Storage & Filesystems

## 📚 Learning Objectives

- Manage disk partitions
- Use LVM for flexible storage
- Mount filesystems
- Monitor disk usage

**Estimated Time:** 3 days  
**Labs:** 3

---

## 💾 Disk Commands

### View Disk Usage

```bash
# Disk free space
df -h
df -h /                    # Specific filesystem

# Directory size
du -sh /var                # Summary
du -sh *                   # All in current dir
du -h --max-depth=1 /var   # Depth limited

# Find large files
du -ah /var | sort -rh | head -20

# Block devices
lsblk
lsblk -f                   # With filesystem info

# Detailed disk info
fdisk -l                   # Partition table
parted -l
```

### Mounting

```bash
# Mount filesystem
sudo mount /dev/sdb1 /mnt
sudo mount -t ext4 /dev/sdb1 /mnt
sudo mount -o ro /dev/sdb1 /mnt    # Read-only

# Unmount
sudo umount /mnt
sudo umount /dev/sdb1

# Check mount points
mount
cat /proc/mounts

# fstab (persistent mounts)
cat /etc/fstab

# Format
sudo mkfs.ext4 /dev/sdb1
sudo mkfs.xfs /dev/sdb1
```

---

## 🔄 LVM (Logical Volume Manager)

### LVM Components

```
Physical Volume (PV) → Volume Group (VG) → Logical Volume (LV)
/dev/sdb               vg_data               lv_storage
```

### LVM Commands

```bash
# Create physical volume
sudo pvcreate /dev/sdb
sudo pvcreate /dev/sdc
sudo pvs                   # View PVs

# Create volume group
sudo vgcreate vg_data /dev/sdb /dev/sdc
sudo vgs                   # View VGs

# Create logical volume
sudo lvcreate -L 10G -n lv_storage vg_data
sudo lvcreate -l 100%FREE -n lv_all vg_data
sudo lvs                   # View LVs

# Format and mount
sudo mkfs.ext4 /dev/vg_data/lv_storage
sudo mkdir /mnt/storage
sudo mount /dev/vg_data/lv_storage /mnt/storage

# Extend volume
sudo lvextend -L +5G /dev/vg_data/lv_storage
sudo resize2fs /dev/vg_data/lv_storage
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
