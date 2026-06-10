# Chapter 10: Security & Hardening

## 📚 Learning Objectives

- Security best practices
- SELinux/AppArmor basics
- System hardening
- Monitor for security

**Estimated Time:** 4 days  
**Labs:** 3

---

## 🔒 Security Basics

### User Security

```bash
# Strong passwords
passwd                      # Change password
sudo passwd username        # Admin change

# Lock/unlock user
sudo usermod -L username    # Lock
sudo usermod -U username    # Unlock

# Password policies
chage -l username           # View password aging
sudo chage -M 90 username   # Max 90 days
```

### File Security

```bash
# Immutable files (can't delete/modify)
sudo chattr +i file         # Set immutable
sudo chattr -i file         # Remove immutable
lsattr file                 # View attributes

# Check for world-writable files
find / -type f -perm -002   # World-writable
find / -type d -perm -002   # World-writable dirs

# SUID/SGID files (security risk)
find / -perm -4000          # SUID files
find / -perm -2000          # SGID files
```

---

## 🛡️ SELinux

```bash
# Check status
getenforce                  # Enforcing/Permissive/Disabled
sestatus

# Change mode (temporary)
sudo setenforce 0           # Permissive
sudo setenforce 1           # Enforcing

# View context
ls -Z file                  # File context
ls -Zd /var/www             # Directory context
id -Z                       # User context

# Modify context
sudo chcon -t httpd_sys_content_t /var/www/file
sudo restorecon -R /var/www

# Manage booleans
getsebool -a | grep http
togglesebool httpd_enable_homedirs
setsebool -P httpd_can_network_connect on
```

---

## 📊 Security Monitoring

```bash
# Last logins
last                        # Successful logins
lastb                       # Failed logins

# Current users
who
w

# Login history
/var/log/wtmp             # Binary file
faillog                   # Failed logins

# Audit commands (auditd)
auditctl -l               # List rules
ausearch -f /etc/passwd   # Search audit log
```

---

## 🔐 SSH Hardening

```bash
# Edit /etc/ssh/sshd_config
Port 2222                 # Non-standard port
PermitRootLogin no        # Disable root login
PasswordAuthentication no # Key auth only
MaxAuthTries 3
ClientAliveInterval 300

# Restart SSH
sudo systemctl restart sshd
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
3. Course complete!
