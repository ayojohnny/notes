# Linux | Package Management - Advanced Package Tool

`apt`
- recommended way to install software packages on Ubuntu & Debian systems
- merged `apt-get` and `apt-cache` tools
- does not understand `.deb` files, works with packages downloaded from repositories
    - calls `dpkg` directly under the hood after downloading `.deb` archives

APT repository
- a web server containing collection of packages w/ metadata readable by `apt` tool

PPA (Personal Package Archive)
- special kind of repository hosted on servers like Launchpad

Only `root` can manage packages

`apt` holds a DB of current APT respositories on the system.
- can get out of date (hence use `apt update`)

`apt update`
- update the APT repository DB on the system
- does not install or remove repositories

`apt install`
- install specified package and all dependencies

`apt full-upgrade`
- remove install packages if needed
- upgrade entire system

`apt remove`
- uninstall packages
- may leave some config files behind

`apt purge`
- remove package and all config files

`apt autoremove`
- auto remove dependencies that are no longer needed anymore

`ls -l /var/cache/apt/archives`
- shows all installed and upgrades packages

`apt clean`
- removes contents of the cache files

```bash
# Install multiple packages (from repository) 
sudo apt install <package1> ... <packageN>

# Install via local APT repo.
sudo apt install path/to/local/apt/target-binary-package.deb
```

```bash
# Get list of upgradeable software
apt list --upgradeable
```

```bash
# Upgrade the system as a whole
sudo apt full-upgrade

sudo apt full-upgrade -y # run non-interactive, assume 'yes'
```
