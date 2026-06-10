# Chapter 8: Storage & Filesystems

## 📚 Learning Objectives

- Disk management
- Mounting
- LVM basics

**Estimated Time:** 3 days  
**Labs:** 3

---

## 💾 Disk Commands

```bash
df -h                   # Disk free space
du -sh /var             # Directory size
lsblk                   # Block devices
fdisk -l                # Partition table
mount /dev/sdb1 /mnt    # Mount filesystem
umount /mnt             # Unmount
```

## 🔄 LVM

```bash
pvcreate /dev/sdb       # Create physical volume
vgcreate vg1 /dev/sdb   # Create volume group
lvcreate -L 10G -n lv1 vg1  # Create logical volume
mkfs.ext4 /dev/vg1/lv1  # Format
mount /dev/vg1/lv1 /mnt # Mount
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
