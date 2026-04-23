# Linux | File System - File Permissions - Changing Persmission - Chmod

`chmod`
- command to change permissions of a file or directory
- use symbolic or numeric (octal) notatoin
- only `root` or file's ownwer can change a file's permissions

Symbolic notation: `chmod [who][OPERATION][permissions] filename`

`who` -> user category whose permissions will be changed
- `u` = user that owns the file
- `g` = the group the file belongs to
- `o` = other users

`Operation`: define what permissions to remove, add, or set
- `-` = remove specified permissions
- `+` = add specified permissions
- `=` = change current permissions to specified permissions

`permissions`:
- `r` = read
- `w` = write
- `x` = execute

```bash
# Symbolic notation

# Remove write permissions to `foobar.txt` for the user (file owner)
chomod u-w foobar.txt 

# Give full permissions to the user (file owner)
chmod u+rwx foobar.txt

# Remove execute from file owrner, make group writable, remove read & write from others
chmod u-x,g+w,o-rw foobar.txt

# Remove read from file owner and group, give file owner execute, give others no permissions.
chmod ug-r,u+x,o-rwx foobar.txt

# Give read to all (owner, group + others), remove write and execute from all.
chmod a+r,a-wx foobar.txt

# User and group get read & write, others have no permissions.
chmod ug=rw, o= foobar.txt
```

```bash
# Octal notation ("absolute changing mode", "numeric notation")

# Give read & write to user, give read to group, give read to other
chmod 644 foobar.txt
```

```bash
# Recursive example (best to avoid this)

mkdir -p foo/bar
touch foo/a.txt foo/bar/b.txt foo/bar/c.txt

chmod -R 750 foo
```
