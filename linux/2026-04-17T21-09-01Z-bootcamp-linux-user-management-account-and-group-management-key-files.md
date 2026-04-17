# Linux | Account & Group Management - Key Files

`/etc/passwd`
- world readable
- holds user account information

`/etc/shadow`
- only readable by `root`
- holds encrypted passwords for user accounts
    - salted + hashed passwords

`/etc/group`
- world readable
- holds information about groups (who is in what group, group id, etc.)

`/etc/gshadow`
- holds passwords for groups

`/etc/login.defs`
- default options for a new user
- applies when running `useradd <username>` without any options

Avoid modifying these files directly. Restore to native commands:
- `useradd`
- `usermod`
- `userdel`

