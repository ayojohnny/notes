# Linux | Software Management

```bash
# Get info about a deb package
sudo dpkg --info google-chrome-stable_current_amd64.deb

# Install package from .deb file
sudo dpkg -i google-chrome-stable_current_amd64.deb

# List all installed packages
sudo dpkg --get-selections
sudo dkpg-query -l

# List all files of specific package
sudo dpkg-query -l | grep ssh
sudo dpkg -L openssh-server

# Find which files belong to a package
sudo dpkg -S /bin/ls
    # coreutils: /bin/cp

# Remove a package
sudo dpkg -r google-chrome-stable
 
# Purge a package
sudo dpkg -P google-chrome-stable
```

```bash
# Update APT repo DB (package index - does not install/remove/update packages)
sudo apt update

# Install or update a package
sudo apt install apackage 2
sudo apt install nginix terraform nvim

# List upgradeable packages
sudo apt list --upgradeable

# Upgrade (and clean) all packages
sudo apt full-upgrade
sudo apt full-upgrade -y # non-interactive

# Remove a package
sudo apt remove nvim

# Purge a package and its configurations.
sudo apt purge nvim

# Remove dependencies that are not needed anymore.
sudo apt autoremove

# Remove the save .deb files from the cache directory (/var/cache/apt/archives)
sudo apt clean

# List all available packages
sudo apt list 

# Show information about a package
sudo apt show nginix

# List all installed packages
sudo apt list --installed
```
