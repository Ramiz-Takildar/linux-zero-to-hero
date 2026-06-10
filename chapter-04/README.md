# Chapter 4: Package Management

## 📚 Learning Objectives

- Use APT and DNF package managers
- Install, update, and remove software
- Manage repositories
- Troubleshoot package issues

**Estimated Time:** 2 days  
**Labs:** 3

---

## 📦 APT (Debian/Ubuntu)

### Basic Commands

```bash
# Update package lists
sudo apt update

# Upgrade installed packages
sudo apt upgrade
sudo apt full-upgrade  # Also removes obsolete packages

# Install package
sudo apt install package
sudo apt install package1 package2

# Remove package
sudo apt remove package           # Keep config
sudo apt purge package            # Remove with config

# Search packages
apt search keyword
apt-cache search keyword

# Show package info
apt show package
apt-cache show package
apt-cache policy package  # Show installed version

# List installed packages
apt list --installed
dpkg -l

# Clean up
sudo apt autoremove               # Remove unused dependencies
sudo apt autoclean                # Clean package cache
sudo apt clean                    # Clear all cache
```

### Repository Management

```bash
# View repositories
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*

# Add repository
sudo add-apt-repository ppa:user/ppa

# Update after adding repo
sudo apt update
```

---

## 📦 DNF/YUM (RHEL/CentOS/Fedora)

### Basic Commands

```bash
# Update packages
sudo dnf update
sudo dnf upgrade

# Install
sudo dnf install package

# Remove
sudo dnf remove package
sudo dnf erase package

# Search
sudo dnf search keyword

# Info
sudo dnf info package

# List
sudo dnf list installed

# Clean
sudo dnf clean all
sudo dnf autoremove
```

### Repository Management

```bash
# List repos
sudo dnf repolist
sudo dnf repolist all

# Enable/disable repo
sudo dnf config-manager --set-enabled repo-name
sudo dnf config-manager --set-disabled repo-name
```

---

## 🆚 APT vs DNF Comparison

| Task | APT (Debian) | DNF (RHEL) |
|------|--------------|------------|
| Update cache | apt update | dnf check-update |
| Upgrade | apt upgrade | dnf update |
| Install | apt install | dnf install |
| Remove | apt remove | dnf remove |
| Search | apt search | dnf search |
| Info | apt show | dnf info |
| Clean | apt autoremove | dnf autoremove |

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
