# Chapter 9: System Administration

## 📚 Learning Objectives

- Monitor system logs
- Schedule tasks with cron
- Manage system services
- Backup and restore data

**Estimated Time:** 3 days  
**Labs:** 3

---

## 📝 Logging

### System Logs

```bash
# View system log
cat /var/log/syslog
cat /var/log/messages    # RHEL/CentOS

# Authentication log
cat /var/log/auth.log    # Debian/Ubuntu
cat /var/log/secure      # RHEL/CentOS

# Follow logs (real-time)
tail -f /var/log/syslog
tail -f /var/log/apache2/access.log

# systemd journal
journalctl                   # All logs
journalctl -u nginx          # Service logs
journalctl -f                # Follow
journalctl --since "1 hour ago"
journalctl --since today
journalctl -p err            # Priority only
```

### Log Rotation

```bash
# Logrotate manages logs
ls /etc/logrotate.d/
cat /etc/logrotate.conf
```

---

## ⏰ Cron

### Crontab Commands

```bash
# Edit crontab
crontab -e

# List entries
crontab -l

# Remove all
crontab -r

# User crontabs stored
ls /var/spool/cron/crontabs/
```

### Time Format

```
* * * * * command
| | | | |
| | | | +----- Day of week (0-7, 0=Sun)
| | | +------- Month (1-12)
| | +--------- Day of month (1-31)
| +----------- Hour (0-23)
+------------- Minute (0-59)
```

### Examples

```bash
# Every minute
* * * * * /script.sh

# Every 5 minutes
*/5 * * * * /script.sh

# Every hour
0 * * * * /script.sh

# 2 AM daily
0 2 * * * /script.sh

# Every Monday at 3 AM
0 3 * * 1 /script.sh

# First day of month
0 0 1 * * /script.sh

# System crontab
# /etc/crontab
# /etc/cron.d/
# /etc/cron.hourly/
# /etc/cron.daily/
```

---

## 💾 Backup

### tar Archive

```bash
# Create archive
tar -czvf backup-$(date +%Y%m%d).tar.gz /path/to/backup

# Extract
tar -xzvf backup.tar.gz
tar -xzvf backup.tar.gz -C /restore/path

# List contents
tar -tzvf backup.tar.gz
```

### rsync

```bash
# Local backup
rsync -av /source/ /backup/

# Remote backup
rsync -avz /source/ user@host:/backup/

# Delete removed files
rsync -av --delete /source/ /backup/

# Dry run
rsync -avn /source/ /backup/
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
