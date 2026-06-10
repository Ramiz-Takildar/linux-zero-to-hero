# Chapter 10 Labs: Security

## Lab 10.1: Check Security

```bash
# Last logins
last | head -10

# Failed logins
sudo lastb | head -10 2>/dev/null || echo "Need root/logging"

# Current users
who
w

# Check sudo access
sudo -l
```

## Lab 10.2: SELinux Status

```bash
# Check if SELinux is installed
getenforce 2>/dev/null && echo "SELinux installed" || echo "Not installed"

# View context (if installed)
ls -Z /etc/passwd 2>/dev/null
```

## Lab 10.3: Audit

```bash
# Check for SUID files
find /usr/bin -perm -4000 2>/dev/null | head -10

# Check immutable attribute
sudo touch /tmp/testfile
sudo chattr +i /tmp/testfile
lsattr /tmp/testfile
sudo chattr -i /tmp/testfile
rm /tmp/testfile
```

## Lab 10.4: Password Policies

```bash
# View password aging
sudo chage -l $USER 2>/dev/null || echo "Use: sudo chage -l username"

# View /etc/shadow (needs sudo)
sudo head -5 /etc/shadow

# Check for empty passwords (should be 'x')
cat /etc/passwd | grep -v ':x:' | head -5

# View password requirements
# cat /etc/pam.d/common-password 2>/dev/null
```

## Lab 10.5: File Integrity

```bash
# Check for world-writeable files
find /tmp -type f -perm -002 2>/dev/null | head -10

# Check for SUID root files
find /usr/bin -user root -perm -4000 2>/dev/null | wc -l

# Check for files with no owner
sudo find / -nouser -o -nogroup 2>/dev/null | head -10

# Check /tmp permissions
ls -ld /tmp
```

## Lab 10.6: SSH Security Check

```bash
# View SSH config (needs sudo)
sudo grep -E "^(Port|PermitRootLogin|PasswordAuthentication)" /etc/ssh/sshd_config

# Check for weak SSH config
# Look for:
# PermitRootLogin yes (should be no)
# PasswordAuthentication yes (ideally keys only)
# Port 22 (consider changing)

# View authorized keys
cat ~/.ssh/authorized_keys 2>/dev/null || echo "No authorized keys"

# Check SSH host keys
ls -la /etc/ssh/ssh_host_*key
```

## Lab 10.7: Service Security

```bash
# List running services
systemctl list-units --type=service --state=running | grep -v systemd | head -15

# Check for services listening on all interfaces
sudo ss -tlnp | grep 0.0.0.0 | head -10

# Check for unnecessary services
# sudo systemctl list-unit-files | grep enabled | grep -E "(telnet|ftp)"
```

## Lab 10.8: AppArmor Status

```bash
# Check AppArmor status
sudo aa-status 2>/dev/null || echo "AppArmor not installed/running"

# View AppArmor profiles
ls /etc/apparmor.d/ 2>/dev/null | head -10

# Compare with SELinux
# Most systems use one or the other
```
