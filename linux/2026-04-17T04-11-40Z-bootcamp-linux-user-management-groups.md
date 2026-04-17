# Linux | User Management - Groups

Group:
- means of sharing permissions/privileges to a set of users

Primary groups:
- ID stored in `/etc/passwd` and group name in `/etc/group`

Secondary groups:
- stored in `/etc/group`

In Linux, files are owned by both a **user** and **group**. When users create a new file, the owner and
group get set to that user's name.

```bash
# Find primary group ID for the user
grep <username> /etc/passwd

# output: student:x:1000:1000:Bob,,,:/home/student:/bin/bash

# Find the group name using the user's primary group ID
grep <primaryGroupIdFromOutput> /etc/group
```

Content of `/etc/group` look like: `<primaryGroupName>:x:<id>:<optionalSetOfUsers>`

`fax:x:21:`
- fax group with primary group ID of 21 and no users

`cdrom:x:24:student`: 
- cdrom group with primary group ID 24 and 1 user (student)
- cdrom is **secondary group** for student. It's an additional group is belongs to other than primary

`adm:x:4:syslog,student,foo,bar`
- adm group with primary group ID 4 and 4 users (student, syslog, foo, bar)
- for each user, `adm` is a **secondary group**

`groups`:
- primary CLI command to check which groups a user belongs to

`id`:
- command showing user's primary group ID, secondary group ids, and user id

```bash
student@ubuntu:~$ groups
# output: student adm cdrom

# print groups that the <user> is part of
student@ubuntu:~$ groups <user>
# output: student: student adm cdrom

student@ubuntu:~$ groups <user>
uid=1000(student) gid=1000(student) groups=1000(student), 4(adm), 24(cdrom)
```
