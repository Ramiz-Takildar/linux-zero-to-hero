# Chapter 9: System Administration

## 📚 Learning Objectives

- Logs
- Cron jobs
- Backups

**Estimated Time:** 3 days  
**Labs:** 3

---

## 📝 Logging

```bash
cat /var/log/syslog     # System log
cat /var/log/auth.log   # Authentication log
journalctl              # Systemd logs
journalctl -u nginx     # Service logs
journalctl -f           # Follow logs
tail -f /var/log/syslog # Follow
```

## ⏰ Cron

```bash
crontab -e              # Edit cron
crontab -l              # List cron

# Format: minute hour day month dayofweek command
# * * * * * /path/to/command

# Examples:
# 0 * * * * /script.sh     # Every hour
# 0 2 * * * /backup.sh     # 2 AM daily
# */5 * * * * /check.sh    # Every 5 minutes
```

## 💾 Backup

```bash
tar -czvf backup.tar.gz /path  # Create tarball
tar -xzvf backup.tar.gz        # Extract
dd if=/dev/sda of=backup.img   # Disk image
rsync -av source/ dest/        # Sync
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
