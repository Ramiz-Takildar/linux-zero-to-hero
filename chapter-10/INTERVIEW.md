# Chapter 10 Interview Questions

## Q1: Permission 777 risk?

**Answer:**

rwxrwxrwx = Anyone can read, write, execute.

**Risks:**
- Data exposure
- Unauthorized modifications
- Malicious code execution

**Maximum safe:** 755 (dirs), 644 (files)

---

## Q2: What is chattr +i?

**Answer:**

Makes file immutable - even root can't delete/modify until -i.

```bash
sudo chattr +i file
sudo rm file  # Permission denied!
sudo chattr -i file
sudo rm file  # Works
```

---

## Q3: SELinux enforcing vs permissive?

| Enforcing | Permissive |
|-----------|------------|
| Blocks violations | Only logs |
| Active protection | Monitoring |
| Production | Debugging |

---

## Q4: SSH hardening recommendations?

1. Disable root login
2. Use key authentication
3. Change default port
4. Limit users
5. Use fail2ban
6. Enable 2FA

---

## Q5: Find recently modified files?

```bash
# Last 24 hours
find / -mtime -1

# Last hour
find / -mmin -60
```
