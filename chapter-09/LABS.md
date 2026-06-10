# Chapter 9 Labs

## Lab 9.1: Logs
```bash
tail -20 /var/log/syslog
journalctl --since "1 hour ago"
```

## Lab 9.2: Cron
```bash
crontab -l
# Add: */5 * * * * echo $(date) >> ~/crontest.log
```

## Lab 9.3: Backup
```bash
tar -czvf ~/backup-$(date +%Y%m%d).tar.gz ~/linux-labs
ls ~/*.tar.gz
```
