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

## Lab 9.4: Log Rotation

```bash
# View logrotate config
cat /etc/logrotate.conf | head -30

# View logrotate.d directory
ls /etc/logrotate.d/

# View specific service logrotate config
cat /etc/logrotate.d/apt 2>/dev/null

# Check log size
sudo du -sh /var/log/* | sort -rh | head -10

# Force log rotation (example)
# sudo logrotate -f /etc/logrotate.d/nginx
```

## Lab 9.5: Systemd Timers (Modern Cron)

```bash
# View systemd timers
systemctl list-timers --all

# View timer details
# systemctl cat apt-daily.timer

# View systemd time sync
systemctl status systemd-timesyncd

# Compare with cron
# Timers offer more flexibility and logging
```

## Lab 9.6: Environment Variables

```bash
# View environment
env | head -20
printenv | head -20

# View specific variable
echo $HOME
echo $PATH
echo $USER

# Check shell
# echo $SHELL
# echo $0

# Set temporary variable
export MY_VAR="test value"
echo $MY_VAR

# View in new shell (should be empty)
bash -c 'echo $MY_VAR'
```

## Lab 9.7: System Time

```bash
# View current time
date
date "+%Y-%m-%d %H:%M:%S"

# View hardware clock
sudo hwclock --show 2>/dev/null || echo "May need sudo"

# View timezone
cat /etc/timezone
timedatectl

# List time zones
timedatectl list-timezones | grep -i new_york
```

## Lab 9.8: Locales

```bash
# View current locale
locale

# View available locales
locale -a | head -20

# Check locale config
cat /etc/default/locale 2>/dev/null || echo "Locale config in different location"

# View character encoding
echo $LANG
```
