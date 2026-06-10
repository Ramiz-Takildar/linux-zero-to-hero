# Chapter 7: Networking

## 📚 Learning Objectives

- IP configuration
- SSH
- Firewall

**Estimated Time:** 3 days  
**Labs:** 3

---

## 🌐 Network Commands

```bash
ip addr                 # IP addresses
ip route                # Routing table
ping google.com         # Test connectivity
traceroute google.com   # Trace route
netstat -tlnp           # Listening ports
ss -tlnp                # Modern netstat
nslookup google.com     # DNS lookup
dig google.com          # Detailed DNS
```

## 🔑 SSH

```bash
ssh user@host           # Connect
scp file user@host:/path  # Copy to remote
scp user@host:/path file  # Copy from remote
```

## 🔥 Firewall (UFW)

```bash
ufw status              # Check status
ufw enable              # Enable
ufw allow 22            # Allow SSH
ufw allow 80/tcp        # Allow HTTP
ufw deny 3306           # Deny MySQL
ufw delete allow 80     # Remove rule
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
