# Linux | Special Permissions - SGID (Set Group ID)

`SGID` mainly for directories.

If SGID on directories, all files or directories created inside the target directory
will be owned by the same group owner of the directory where SGID was configured.

Use cases:
- created shared direcotires (where writable at group level)

```bash
# Absolute Mode
chmod 2XXX foobar/

# Relative Mode
chmod g+s foobar/


ls -ld /foobar/
# drwxrws--- 2 pr1 programmers 4096 iul 14 13:15 foobar/
```

```bash

# Become `root` to create new users.
sudo su

groupadd programmers
useradd -s /bin/bash peter
useradd -s /bin/bash james

usermod -aG programmers peter
usermod -aG programmers james

groups peter
# peter : peter programmers

groups james
# james : james programmers

mkdir /shared-programming-folder

# Make peter the file owner, but dir open to anyone in programmers group.
chown peter:programmers /shared-programming-folder

ls -ld /shared-programming-folder 
# drwxr-xr-x 2 peter programmers 4096 aug 3 13:20 /shared-programming-folder

# Become beter & create a file in the shared folder.
sudo su peter
cd /shared-programming-folder
touch hello.txt

# Currently only peter can access and write to this file.
# Other users in `programming` group can only read.
ls -l 
# -rw-rw-r-- 1 peter peter 0 aug 3 13:21 hello.txt 

exit # go ack to root
chmod 2770 /shared-programming-folder

ls -ld /shared-programming-folder
- drwxrws--- 2 peter programmers 4086 aug 3 13:21 /shared-programming-folder

# become another user in the group
sudo su james

cd /shared-programming/folder

touch from-james.txt
mkdir jesus holy-spirit

# Notice here, the group is `programmers` instead of `james`.
# Anyone in this group can only work in this file.
ls -l
#drwxrwsr-x 2 james programmers 4096 aug 3 13:25 jesus/
#drwxrwsr-x 2 james programmers 4096 aug 3 13:25 holy-spirit/
-rw-rw-r-- 1 peter programmers  4096 aug 3 13:21 hello.txt
-rw-rw-r-- 1 james programmers  4096 aug 3 13:24 from-james.txt
```



