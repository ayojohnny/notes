# Linux | File System - Default Permissions - umask

`umask`:
- sets default file permissions on created resources
- new defaults applied to files & dirs created after the umask change happens (not retroactive)
- only for current user and the current shell session (closing shell or logging out resets to default 0777/0666 respective)

To permanently edit the umask config for a user, add a line in `.bashrc` (or shell config)
and set the umask.

```bash
mkdir foobar/
touch barbaz.txt

# Default permission: 775
drwxrwxr-x 2 student student 4096 aug 3 13:43 foobar/

# Default permission: 664
-rw-rw-r-- 1 student student 0    aug 3 13:43 barbaz.txt
```

Default Permission  | Resource Type     | Umask     | Assigned Default
---                 | ---               | ---       | ---
0777                | directory         | 0002      | 0775
0777                | directory         | 0002      | 0775
0666                | file              | 0002      | 0664
0666                | file              | 0022      | 0644

```bash
# Showing umask value.
umask
# 0002
```
