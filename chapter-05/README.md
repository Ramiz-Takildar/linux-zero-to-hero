# Chapter 5: Process Management

## 📚 Learning Objectives

- View and manage processes
- Understand systemd
- Control system services
- Monitor system performance

**Estimated Time:** 3 days  
**Labs:** 3

---

## 🔍 Process Information

### ps (Process Status)

```bash
# Basic
ps

# Full format
ps aux

# User format
ps -ef

# Specific user
ps -u username

# Tree view
ps auxf
pstree

# Columns explained
# USER: Owner
# PID: Process ID
# %CPU: CPU usage
# %MEM: Memory usage
# VSZ: Virtual memory
# RSS: Resident memory
# TTY: Terminal
# STAT: Status
# START: Start time
# TIME: CPU time
# COMMAND: Command
```

### top / htop

```bash
top              # Interactive process viewer

# In top:
# q: quit
# k: kill process
# r: renice
# M: sort by memory
# P: sort by CPU

htop             # Enhanced top (install first)
```

---

## ⚡ Process Control

### Signals

```bash
kill PID         # SIGTERM (15) - graceful
kill -9 PID      # SIGKILL (9) - force
kill -1 PID      # SIGHUP (1) - reload

# Common signals
# 1  (SIGHUP) - Hang up, reload config
# 9  (SIGKILL) - Kill immediately
# 15 (SIGTERM) - Terminate gracefully
# 18 (SIGCONT) - Continue
# 19 (SIGSTOP) - Stop
```

### Kill Commands

```bash
kill PID         # By PID
killall name     # By name
pkill pattern    # By pattern
pkill -f pattern # Match full command line

# Examples
pkill nginx
killall -9 firefox
```

---

## 🔄 Systemd

### Service Management

```bash
# Check status
sudo systemctl status service

# Start/Stop/Restart
sudo systemctl start service
sudo systemctl stop service
sudo systemctl restart service
sudo systemctl reload service   # Reload config

# Enable/Disable (boot behavior)
sudo systemctl enable service   # Start on boot
sudo systemctl disable service  # Don't start on boot

# Check if enabled
systemctl is-enabled service
```

### Other systemctl Commands

```bash
# List all services
systemctl list-units --type=service

# List running services
systemctl list-units --type=service --state=running

# Failed services
systemctl --failed

# View logs
sudo journalctl -u service
sudo journalctl -u service -f  # Follow
```

---

## 🎯 Background/Foreground

```bash
# Run in background
command &

# Suspend running process
Ctrl+Z

# Background suspended process
bg

# Foreground background process
fg

# Jobs list
jobs

# Bring specific job to foreground
fg %1
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview