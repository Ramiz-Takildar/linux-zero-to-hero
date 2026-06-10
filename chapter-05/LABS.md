# Chapter 5 Labs: Process Management

## Lab 5.1: View Processes

```bash
# View all processes
ps aux | head -20

# Find specific process
ps aux | grep ssh

# Use pgrep
pgrep ssh
pgrep -a ssh  # Show full command

# View tree
pstree | head -20
```

## Lab 5.2: Process Control

```bash
# Create background process
sleep 300 &
PID=$!
echo $PID

# Check process
ps aux | grep sleep

# Kill it
kill $PID

# Verify
ps aux | grep sleep
```

## Lab 5.3: Systemd Services

```bash
# Check SSH service status
sudo systemctl status ssh

# Restart SSH (if you have SSH, be careful!)
# sudo systemctl restart ssh

# List running services
systemctl list-units --type=service --state=running | head -10

# View logs
sudo journalctl -u ssh --no-pager | tail -20
```

## Lab 5.4: Background Jobs

```bash
# Start process
sleep 60
# Press Ctrl+Z

# Check jobs
jobs

# Resume in background
bg

# Check again
jobs

# Bring to foreground
fg
# Then Ctrl+C to end
```
