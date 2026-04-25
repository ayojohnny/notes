# Linux | File System - File Attributes

File permissions:
- only basic security and access control

Linux has other, more advanced control features:
- Access Control Lists (ACLs)
- Attributes

Attributes:
- define properties of the file
- depend on support of underlying file system (ext4, etc.)
- distinct from other metadata about file (file permissions, owner, group, etc.)
- can have 1 of 2 states:
    1. set
    2. cleared

`lsattr`
- show attributes of a file
- many different attributes (each represented by a character or `-`)

`chattr`
- change attributes on a file or directory

```bash
lsattr

-----------e----- hello.txt

sudo su # become root

# Make hello.txt append only (including root)
chattr +a hello.txt

----a-------e---- hello.txt
```

