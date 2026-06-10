# Chapter 3: Users & Permissions

## 📚 Learning Objectives

- User and group management
- File permissions and ownership
- Special permissions (SUID, SGID, Sticky)
- sudo configuration
- Access Control Lists (ACL)

**Estimated Time:** 2 days  
**Labs:** 3

---

## 👤 User Management

### User Commands

```bash
# Add user
sudo useradd username
sudo adduser username    # Interactive (Debian/Ubuntu)

# Set password
sudo passwd username

# Modify user
sudo usermod -aG group user    # Add to group
sudo usermod -g primary user   # Change primary group
sudo usermod -s /bin/bash user # Change shell
sudo usermod -d /newhome user  # Change home
sudo usermod -L user           # Lock account
sudo usermod -U user           # Unlock account

# Delete user
sudo userdel username
sudo userdel -r username       # Remove home too

# View user info
id username
groups username
whoami
who
w
finger username
```

### User Files

```bash
/etc/passwd      # User account info
/etc/shadow      # Encrypted passwords
/etc/group       # Group information
/etc/gshadow     # Secure group info
```

---

## 🔐 File Permissions

### Permission Basics

```
-rwxr-xr-- 1 owner group size date filename
 |  |  |
 |  |  +--- Others (r--)
 |  +------ Group (r-x)
 +--------- Owner (rwx)
```

### chmod (Change Mode)

```bash
# Numeric mode
chmod 755 file      # rwxr-xr-x
chmod 644 file      # rw-r--r--
chmod 600 file      # rw-------
chmod 777 file      # rwxrwxrwx (DANGEROUS)

# Symbolic mode
chmod u+x file      # Add execute for owner
chmod g-w file      # Remove write for group
chmod o=r file      # Set read only for others
chmod a+x file      # Add execute for all
```

### chown (Change Owner)

```bash
sudo chown user file           # Change owner
sudo chown :group file         # Change group
sudo chown user:group file     # Change both
sudo chown -R user:dir         # Recursive
```

---

## ⭐ Special Permissions

### SUID (Set User ID)

```bash
chmod u+s file      # -rwsr-xr-x
chmod 4755 file
```

- File executes with owner's privileges
- Dangerous if misused

### SGID (Set Group ID)

```bash
chmod g+s file      # -rwxr-sr-x
chmod 2755 file
```

- File executes with group's privileges
- On directory: new files inherit group

### Sticky Bit

```bash
chmod +t /tmp       # drwxrwxrwt
chmod 1777 /tmp
```

- Only owner can delete files in directory
- Used on /tmp

---

## 🛡️ sudo

### sudo Usage

```bash
sudo command             # Run as root
sudo -u username command # Run as specific user
sudo -i                  # Interactive root shell
sudo -s                  # Root shell with env
```

### sudoers Configuration

```bash
# Edit sudoers (use visudo!)
sudo visudo

# Add user
username ALL=(ALL:ALL) ALL

# Add group
%admin ALL=(ALL) NOPASSWD:ALL

# Specific commands
username ALL=(root) /bin/systemctl restart nginx
```

---

## 🔐 ACL (Access Control Lists)

```bash
# Check ACL
getfacl file

# Set ACL
setfacl -m u:username:rw file
setfacl -m g:groupname:r file

# Remove ACL
setfacl -x u:username file

# Remove all ACL
setfacl -b file

# Set default ACL on directory
setfacl -d -m u:username:rx directory/
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
