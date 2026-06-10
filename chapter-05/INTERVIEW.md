# Chapter 5 Interview Questions

## Q1: ps aux columns meaning?

**Answer:**

| Column | Meaning |
|--------|---------|
| USER | Owner |
| PID | Process ID |
| %CPU | CPU usage |
| %MEM | Memory usage |
| VSZ | Virtual memory size |
| RSS | Resident set size |
| TTY | Terminal |
| STAT | Process status |
| START | Start time |
| COMMAND | Command line |

---

## Q2: kill vs kill -9?

| kill | kill -9 |
|------|---------|
| SIGTERM (15) | SIGKILL (9) |
| Graceful shutdown | Immediate |
| Can be caught/ignored | Cannot be caught |
| Cleanup allowed | No cleanup |

**Best practice:** Try kill first, then kill -9 if needed

---

## Q3: What is systemd?

**Answer:**

Linux system and service manager that:
- Replaces traditional init
- Manages services (start/stop)
- Handles logging (journald)
- Parallel startup for faster boot

---

## Q4: Difference between systemctl reload and restart?

| reload | restart |
|--------|---------|
| Reload config | Stop and start process |
| No downtime | Brief downtime |
| Not all services support | Always works |

---

## Q5: Find zombie processes?

```bash
ps aux | grep 'Z'
# STAT column shows Z
```

**Zombie:** Process finished but parent didn't read exit status
