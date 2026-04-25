# Linux | File Permissions - Special - Set Uiser ID (SUID)

Besides `r` (read), `w` (write), and `x` (execute) files and directories can have the follow special permissions:
1. SUID - set user id
2. SGID - set group ID
3. Sticky Bit

By default a program in Linux runs with the permissions of the user who executes/invokes the program.

When a program (executable file) that has SUID special permission set, the resulting process has the
permissions of the owner of the command, not the permissions fo teh user who executes the command.

For instance, if `cat` program/binary/cmd has the `s` bit set for user (i.e. `-rwsr-xr-x`) then anyone who
runs `cat` would be running it as if they were `root` permissions.

```bash
# Setting SUID: Absolute Mode
chmod 4XXX foobar.txt
chmod u+s foobar.txt

# -rwsr-xr-x 1 root root 68208 apr 16 15:36 /foobar.txt
```
SUID :
- `s` = executable permissions on the file      (`-rws------`)
- `S` = no executable permissions on the file   (`-rwS------`)


Be extremely careful with SUID, SGID, and Sticky Bit.
- easy to break security

Some commands (i.e. `passwd`) need to be ran as `root` to be effective.


`find /usr/bin/ -perm -4000` find all files that have atleast `s` (elevated privileges) set.

