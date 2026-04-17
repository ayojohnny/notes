# Linux | Account Management - Modify User

`usermod`
- same options as `useradd`
- modifies `/etc/passwd` instead of adding a new line

`groups`
- list the groups for a user

```bash
# Change description about acocunt `james`
sudo usermod -c "Goland developer" james

# Change primary for `james` to `daemon`
sudo usermod -g daemon james

groups james 
# output -> james : daemon adm mail sudo


# Completely change `james` groups (will overwrite)
# This does not change the primary group. James's primary group
# would still be `daemon` from earlier.
sudo usermod -G developers, managers james


# Append to groups to james current groups
sudo usermod -aG sudo,mail,adm james
# output -> james : daemon developers manager sudo mail adm 
```

For the second approach, the group must already exist.

