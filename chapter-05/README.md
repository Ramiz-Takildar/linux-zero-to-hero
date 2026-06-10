# Chapter 5: Process Management

## 📚 Learning Objectives

- View and manage processes
- Systemd services

**Estimated Time:** 3 days  
**Labs:** 3

---

## ⚙️ Process Commands

```bash
ps aux                  # List all processes
top                     # Interactive view
htop                    # Enhanced top (install first)
kill PID                # Kill process
kill -9 PID             # Force kill
pkill name              # Kill by name
pgrep name              # Find PID by name
```

## 🔄 Systemd

```bash
systemctl status service
systemctl start service
systemctl stop service
systemctl restart service
systemctl enable service   # Auto-start
systemctl disable service  # Disable auto-start
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
