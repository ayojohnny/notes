# Linux | Account Management - Delete User Account

`userdel`
- deletes a user only if no other user on the system is in it's group
- does not remove home or mail (spool) direcotires
- low-level command

`deluser`
- comes on ubuntu & debian distros
- "friendly" wrapper around `userdel`

Deletion workflow:
1. delete user
2. delete user's home directory & associated files 

