# Chapter 7 Labs: Networking

## Lab 7.1: Network Info

```bash
# View interfaces
ip addr

# View specific interface
ip addr show lo

# Test connectivity
ping -c 3 google.com

# DNS lookup
dig google.com +short
host google.com
```

## Lab 7.2: SSH Keys

```bash
# Generate key (skip if already have)
# ssh-keygen -t ed25519

# View public key
cat ~/.ssh/id_rsa.pub 2>/dev/null || cat ~/.ssh/id_ed25519.pub 2>/dev/null

# Test SSH (if you have another server)
# ssh user@server

# Copy file via SCP (example)
# scp test.txt user@server:/tmp/
```

## Lab 7.3: Firewall

```bash
# Check status
sudo ufw status

# Enable if not already
# sudo ufw enable

# Allow SSH
sudo ufw allow 22

# Check rules
sudo ufw status verbose
```

## Lab 7.4: Network Troubleshooting

```bash
# Check routing table
ip route
ip route | grep default

# Check DNS configuration
cat /etc/resolv.conf

# Test name resolution
nslookup google.com
dig google.com +short

# Trace route (if installed)
which traceroute || sudo apt install -y traceroute
traceroute -m 5 google.com

# Check listening ports
sudo ss -tlnp
sudo netstat -tlnp 2>/dev/null || echo "netstat not installed"

# Check established connections
ss -tn state established
```

## Lab 7.5: SSH Configuration

```bash
# View SSH config
cat ~/.ssh/config 2>/dev/null || echo "No personal config"

# View SSH client config
ls /etc/ssh/ssh_config

# View SSH server config (needs sudo)
sudo head -20 /etc/ssh/sshd_config

# Check SSH service
sudo systemctl status ssh

# Test SSH config syntax
sudo sshd -t
```

## Lab 7.6: Netcat Testing

```bash
# Install netcat
which nc || sudo apt install -y netcat-traditional

# Test TCP port
nc -zv google.com 443
nc -zv google.com 80

# Test UDP port (may not respond)
nc -zvu 8.8.8.8 53

# Simple port scan
nc -zv localhost 1-1000 2>&1 | grep succeeded
```

## Lab 7.7: Network Statistics

```bash
# Interface statistics
ip -s link

# Socket statistics
ss -s

# Network counters
cat /proc/net/dev

# ARP table
ip neigh
```
