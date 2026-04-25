# Linux | File System - Special Permissions - Sticky Bit

Sticky Bit
- applied to directories

User may only delete files she owns or for which she has explicit **write permission**
granted... even when she has write access to the directory.

Allows creation of a directory that everyone can use as shared file storaged.
Files are protected because no one can delete anyone else's files.

```bash
# Absolute Mode
chmod chmod 1xxx foobar/

# Relative Mode
chmod chmod o+t foobar/

ls -ld /foobar/
# drwxrwxrwt 2 root root 4096 iul 14 13:45 foobar/
```

```bash
sudo su

mkdir testing/
chmod 777 testing
ls -ld testing
# drwxrwxrwx 2 root root 4096 aug 3 13:33 testing/

# A random user creates files inside `testing/`.
touch foobar{1..2}.txt

# Thinking 600 to prevent modification, reading, or running these
# files from other others. 
#
# However, this is wrong. Since the parent directory has write permissions
# then these files (despite having -rw------- permissions) are still writable
# by any user.
chmod 600 foobar1.txt
chmod 600 foobar2.txt

# Because directory has rw permission, then files inside are writable.
ls -ld testing/
# drwxrwxrwx 2 root root 4096 Augh 3 13:34 .


## Setting the sticky bit on the directory.
chmod 1777 /testing/
ls -ld testing
# drwxrwxrwt 2 root root 4096 aug 3 13:36 testing/
```

The whole purpof of sticky bit is to create shared folders where files cannot be
deleted by users who don't own the file.
