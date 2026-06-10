# Chapter 4 Labs: Package Management

## Lab 4.1: APT Operations

```bash
# Update package lists
sudo apt update

# Show number of available updates
apt list --upgradable 2>/dev/null | wc -l

# Install a package
sudo apt install -y htop
which htop

# Show package info
apt show htop

# List files in package
# dpkg -L htop
```

## Lab 4.2: Search and Clean

```bash
# Search for packages
apt search "monitor" | head -20

# Check if package is installed
dpkg -l | grep nginx

# Dry run remove
sudo apt remove --dry-run htop

# Actually remove
sudo apt remove -y htop

# Clean up
sudo apt autoremove -y
sudo apt autoclean
```

## Lab 4.3: Repository Info

```bash
# View sources
cat /etc/apt/sources.list | head -5

# View additional sources
ls /etc/apt/sources.list.d/

# Update should be run after changes
sudo apt update
```
