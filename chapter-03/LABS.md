# Chapter 3 Labs

## Lab 3.1: Permissions
```bash
touch perm.txt
chmod 600 perm.txt
ls -l perm.txt
```

## Lab 3.2: Users
```bash
# As root or with sudo
sudo useradd testuser
sudo passwd testuser
id testuser
```

## Lab 3.3: Ownership
```bash
sudo chown root:root perm.txt
ls -l perm.txt
```
