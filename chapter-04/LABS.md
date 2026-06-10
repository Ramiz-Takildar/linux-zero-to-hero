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

## Lab 4.4: Package Dependencies

```bash
# View package dependencies
apt-cache depends nginx | head -20

# View reverse dependencies (what depends on this)
apt-cache rdepends curl | head -10

# Show package policy/versions
apt-cache policy htop

# Download package without installing
apt download curl
ls curl*.deb

# Clean up
rm curl*.deb 2>/dev/null || true
```

## Lab 4.5: Hold and Unhold Packages

```bash
# Install a test package
sudo apt install -y figlet

# Check version
figlet --version

# Hold the package (prevent updates)
sudo apt-mark hold figlet
apt-mark showhold

# Try to upgrade (will skip held package)
sudo apt upgrade -y

# Unhold the package
sudo apt-mark unhold figlet

# Remove test package
sudo apt remove -y figlet
```

## Lab 4.6: DPKG Operations

```bash
# List all installed packages
dpkg -l | wc -l
dpkg -l | grep ^i | wc -l  # Only installed

# Show package status
dpkg -l ssh

# Search for package owning a file
dpkg -S /bin/ls
dpkg -S /usr/bin/htop 2>/dev/null || echo "Not found"

# Reconfigure package
# sudo dpkg-reconfigure tzdata

# Check for broken packages
sudo dpkg --audit
```
