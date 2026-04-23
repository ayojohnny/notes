# Linux | File System - File Permissions

File permissions (or "file modes")
- determine who can access, change, or execute a file on a Linux system

Each file and directory has an **owner** and a **group**. Default owner is
the user who creates the file. The group is the *primary group* of the user.

`chown`: change ownership of a file or directory
`chgrp`: change group ownership of a file or directory

Only `root` can run `chown` and `chgrp` commands

Each file (or directory) has 3 categories of permissions:
1. File owner
2. Group owner
3. Other (anyone else or the whole world)

The File Permissions
- `r` -> read permission
- `w` -> write permission
- `x` -> execute permission

Example of file persmission

```bash
-rw-r--r-- 1 root root 2972 aug 2 14:38 /etc/passwd

# 1st bit    -> tells what time of file (directory, file, pipe, etc.)
# 2nd -> 4th -> user permissions
# 5th -> 7th -> group permissions
# 7th -> 9th -> other permissions (world permissions)
```

```bash
# The following are methods of viewing file permissions.
ls -l /etc/passwd
stat /etc/passwd
```

IMPORTANT: file permissions are not applicable to `root`.
- `root` can modify any file on the system, regardless of permissions.

