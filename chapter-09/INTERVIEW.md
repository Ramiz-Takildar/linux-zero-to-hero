# Chapter 9 Interview Questions

## Q1: Where are logs stored?

| Log Type | Debian/Ubuntu | RHEL/CentOS |
|----------|---------------|-------------|
| System | /var/log/syslog | /var/log/messages |
| Auth | /var/log/auth.log | /var/log/secure |
| Boot | /var/log/boot.log | journalctl |

---

## Q2: Cron time format?

```
* * * * * command
| | | | |
| | | | +-- Day of week (0-7)
| | | +---- Month (1-12)
| | +------ Day (1-31)
| +-------- Hour (0-23)
+---------- Minute (0-59)
```

---

## Q3: rsync vs scp?

| rsync | scp |
|-------|-----|
| Delta transfer | Full copy |
| Resume support | No resume |
| Faster | Simpler |
| Remote sync | One-time copy |

---

## Q4: Run cron job every 5 minutes?

```bash
*/5 * * * * /path/to/script.sh
```

---

## Q5: journalctl vs syslog?

| journalctl | syslog |
|------------|--------|
| systemd | traditional |
| Binary format | Text files |
| More features | Universal |
