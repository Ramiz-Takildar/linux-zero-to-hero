# Chapter 7 Labs

## Lab 7.1: Network Info
```bash
ip addr
ip route
ping -c 3 google.com
```

## Lab 7.2: Port Check
```bash
sudo ss -tlnp
netstat -tlnp 2>/dev/null || echo "Install net-tools"
```

## Lab 7.3: Firewall
```bash
sudo ufw status
sudo ufw allow 8080
sudo ufw status numbered
```
