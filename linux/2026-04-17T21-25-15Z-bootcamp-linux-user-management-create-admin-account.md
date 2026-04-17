# Linux | User Management - Create Admin Account

By default only the user created at installation time can run commands as admin level

`sudo` -> used on debian based distros
`wheel` -> use on CentOS and RedHat based distros

In use in the `sudo` group can run administrative commands.

```bash
sudo useradd -m -s /bin/bash sonic

sudo passwd sonic
# Password - hedgehog

# Add sonic to sudo group - enable admin level commands
sudo usermod -aG sudo sonic

su sonic # switch to sonic account

# verify sonic can use adin-level commands
sonic@host: ~$ sudo cat /etc/shadow
```
