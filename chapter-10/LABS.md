# Chapter 10 Labs

## Lab 10.1: Security Check
```bash
last | head -10
whoami
id
```

## Lab 10.2: SELinux Status
```bash
getenforce 2>/dev/null || echo "SELinux not installed"
```

## Lab 10.3: Audit
```bash
sudo cat /var/log/auth.log | grep sudo | tail -10
```
