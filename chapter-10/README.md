# Chapter 10: Security & Hardening

## 📚 Learning Objectives

- Security best practices
- SELinux/AppArmor
- Monitoring

**Estimated Time:** 4 days  
**Labs:** 3

---

## 🔒 Security Basics

```bash
passwd                  # Change password
sudo visudo             # Edit sudoers
chattr +i file          # Immutable file
fail2ban-client status  # Fail2ban status
```

## 🛡️ SELinux

```bash
getenforce              # Check status
setenforce 0            # Permissive
setenforce 1            # Enforcing
ls -Z file              # View context
chcon -t type file      # Change context
```

## 📊 Monitoring

```bash
last                    # Login history
lastb                   # Failed logins
who                     # Current users
w                       # Who and what
dmesg                   # Kernel messages
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
3. Course complete!
