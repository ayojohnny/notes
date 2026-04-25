# Linux | File Ownership - Chown & chgrp

All files in Linux belong to an **owner** and a **group**

`chgrp`:
- change the group of a file

`chown`:
- change the owner of a file

Normal users:
- change group of file only if they own the file & only to a group which they are a member of

`root` user:
- change change the group ownership of all files

```bash
ls -l hello.c
# -rw-r--r-- 1 root root 81 uil 17 12:49 hello.c

chwon james hello.c
ls -l hello.c
# -rw-r--r-- 1 james root 81 iul 18 12:49 hello.c

chgrp adm hello.c
# -rw-r--r-- 1 james adm 81 iul 12:49 hello.c
```

```bash
sudo chown foobar hello.c world.c examples/ # Change ownership of the files to `foobar`

# When using <UID> for ownership change, always make a number.
# This prevents getting mixed up with a user account who might
# have a numeric name similar to UID (i.e. user account called 105,
# and trying to change owner to UID 105 (which points to user bob).
sudo chown +<UID> cpu.txt # Change permission to UID
```

```bash
# Changes owner to foo and group to bar for hello.c file.
sudo chown foo:bar hello.c

# Change group.
sudo chgrp foobargroup hello.c

# Change only group via `chown` cmd.
sudo chown :foobargroup hello.c
```

```bash
# Recursively change permissions for contents in teh directory.
sudo chown -R student:student some_directory/
```
