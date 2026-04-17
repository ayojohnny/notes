# Linux | User Account Monitoring

User account monitoring:
- seeing what users are logged into the system and seeing what those users do

In Linux, you can login as user A then swap to user B via the `su` command.

Real ID: the user who initially logs int (RUID)
Effective ID: the current user in the shell (EUID)

`whoami`
- print username of the current EUID
- same as `id -un`

`who`
- dispay username of initially logged in user (RUID)
- parses and displays contents of `/var/run/utmp`

`w`
- more context about logged in users

`id`
- print effective user and its groups

`/var/log/wtmp`
- maintains logs of all logged in and logged out users in the past 

`uptime`
- shows uptime of the running system (load average, users logged in, etc.)

`last`
- show list of last logged in users
- reads the `/var/log/wtmp` file
- prints logins & logouts of users (in reverse time order)

```bash
# Print last login and logout attempts of <user>
last <user>
```
