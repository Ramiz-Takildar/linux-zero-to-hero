# Chapter 9 Labs: System Administration

## Lab 9.1: Logs

```bash
# View system logs
sudo tail -20 /var/log/syslog 2>/dev/null || sudo tail -20 /var/log/messages

# View auth logs
sudo tail -20 /var/log/auth.log 2>/dev/null || sudo tail -20 /var/log/secure

# Journalctl
sudo journalctl --since "1 hour ago" | tail -20
```

## Lab 9.2: Cron

```bash
# Edit crontab
crontab -l

# Add entry (don't save unless you want it)
# crontab -e
# Add: */5 * * * * echo $(date) >> ~/cron-test.log

# View system cron
ls /etc/cron.d/
cat /etc/crontab | head -20
```

## Lab 9.3: Backup

```bash
# Create backup directory
mkdir -p ~/backups

# Create tar backup
cd ~
tar -czvf ~/backups/home-backup-$(date +%Y%m%d).tar.gz linux-labs

# Verify
ls -lh ~/backups/
tar -tzvf ~/backups/home-backup-*.tar.gz | head
```
