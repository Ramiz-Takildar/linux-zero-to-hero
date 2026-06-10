# Chapter 7: Networking

## 📚 Learning Objectives

- Configure network interfaces
- Use SSH for remote access
- Manage firewall rules
- Troubleshoot connectivity

**Estimated Time:** 3 days  
**Labs:** 3

---

## 🌐 Network Commands

### View Network Configuration

```bash
# Modern ip command (replaces ifconfig)
ip addr                    # Show interfaces
ip addr show eth0          # Specific interface
ip link                    # Layer 2 info
ip link set eth0 up        # Enable interface
ip link set eth0 down      # Disable interface

# Routing
ip route                   # Show routing table
ip route add 10.0.0.0/8 via 192.168.1.1

# Legacy ifconfig
ifconfig                   # Show all interfaces
ifconfig eth0              # Specific interface
```

### Connectivity Testing

```bash
# Ping (basic connectivity)
ping google.com
ping -c 4 google.com       # Count 4 packets
ping -i 0.5 google.com     # Faster interval

# Traceroute (path trace)
traceroute google.com
tracepath google.com

# DNS lookup
host google.com
nslookup google.com
dig google.com
dig +short google.com

# Port scanning
nc -zv host 80             # Check single port
nc -zv host 1-1000         # Scan range
```

---

## 🔐 SSH

### Basic SSH Usage

```bash
# Connect to remote
ssh user@hostname
ssh user@192.168.1.100
ssh -p 2222 user@host      # Custom port

# Execute command
ssh user@host "ls -la"

# Copy files (SCP)
scp file.txt user@host:/path/
scp -r directory user@host:/path/
scp user@host:/file.txt ./local/

# SSH key generation
ssh-keygen -t rsa -b 4096 -C "comment"
ssh-keygen -t ed25519

# Copy public key
cat ~/.ssh/id_rsa.pub | ssh user@host "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
# or
ssh-copy-id user@host

# SSH config file
# ~/.ssh/config
Host myserver
    HostName 192.168.1.100
    User username
    Port 2222
    IdentityFile ~/.ssh/id_rsa

# Then connect with
ssh myserver
```

---

## 🔥 Firewall (UFW)

```bash
# Check status
sudo ufw status
sudo ufw status verbose

# Enable/disable
sudo ufw enable
sudo ufw disable

# Default policies
sudo ufw default deny incoming
sudo ufw default allow outgoing

# Allow/deny ports
sudo ufw allow 22            # SSH
sudo ufw allow 80            # HTTP
sudo ufw allow 443           # HTTPS
sudo ufw allow 8080          # Custom
sudo ufw deny 3306           # Deny MySQL

# Delete rules
sudo ufw delete allow 80
sudo ufw status numbered
sudo ufw delete 3

# Advanced
sudo ufw allow from 192.168.1.0/24 to any port 22
sudo ufw allow proto tcp from any to any port 80

# Logging
sudo ufw logging on
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
