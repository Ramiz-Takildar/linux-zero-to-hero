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
