# Linux | Linux - Filesystem - Directory Permissions

```bash
# Check permissions on a directory.
ls -ld foobar/

# Giving read permissions to dir.
chmod 400 foobar/ 
```

Read permission:
- can list file contents
- cannot create or delete files
- cannot move into the directory

Read + Write permission:
- same as read

Read + Write + Execute permission:
- can move into the directory
- can create & remove files inside the directory

Directory permissions trump files permissions times.

```bash
mkdir testing/
chmod 700 testing/

touch testing/foobar.txt
chmod 000 testing/foobar.txt # no permissions

# Able to remove foobar due to parent dir permissions, despite
# not having no permissions on the file.
rm testing/foobar.txt 
```
