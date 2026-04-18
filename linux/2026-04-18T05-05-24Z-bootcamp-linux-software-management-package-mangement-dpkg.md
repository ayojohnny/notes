# Linux | Software Management - dpkg 

Most software in Linux is open source. To "install" and use the software one can:
1. download source code and compile it locally
2. install a **binary package** 

Executable:
- outcome of a program's compilation process

`.deb`
- installation package format used on all Debian based distros.
- archive file containing all files and executables needed to run the app/prgram (i.e. binary package)

Installation of software can happen via:
1. GUI 
2. low-level package management tools  (e.g. `dpkg`)
3. high-level package management tools (e.g. `apt`, `apt-get`, via the package manger on the distro)

`dpkg`
- lowest level infrastructure for package mangaement
- dpkg DB has a list of all installed software on the system
- can work with local `.deb` package files
- does not need to know about repositories
- does not resolve/solve dependency issues or conflicts
- best to avoid using this command direclty unless necessary (let higher level tooling handle it)

`apt`
- more "advanced" package management tool on Debian based systems
- uses `dpkg` under the hood

Must be a `sudoer` (superuser/admin) to install packages.

 ```bash
# Assume google-chrome-stable_current_amd64.deb exists on system. It
# has not been installed yet.

dpkg --info google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb # Install
```

```bash
# show all installed software on system
dpkg --get-selections 

```

```bash
# query archtecture and version of installs
dpkg-query -l 
```

```bash
# Show all files related to this install and their paths.
dpkg -L google-chrome-stable_current_amd64.deb
```

```bash
# See what package a specific package belongs to.
dpkg -S /bin/ls  (output -> coreutil: /bin/ls)
``` 

```bash
# Remove google chrome (does not remove config files).
sudo dpkg -r google-chrome-stable

# Purge the application and it's config.
sudo dpkg -P gooogle-chrome-stable
```
