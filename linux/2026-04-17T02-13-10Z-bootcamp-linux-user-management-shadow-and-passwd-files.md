# Linux | User Management - Shadow and Passwd Files

`/etc/passwd`
- info about each account on the system (system, user, etc.)
- anyone can read it (given they have permissions)
- each entry made up of 7 fields:
    1. user's login name
    2. `x` to show password has been saved in `shadow` file (if no x, password not required to log in)
    3. user id
    4. group id
    5. comment (sometimes left blank)
    6. user's home directory path
    7. user's default shell 

If user's shell (slot 7) is `/nologin` or `/false`, it means that user account cannot login.

`/etc/shadow`
- stores actual passwords for users (encrypted)
- can only be read by `root` user
- each entry made up of 9 fields
    1. user name (the link to entries in `/etc/passwd`)
    2. the password

Fields 3-7 are related to password metadata such as: expiratino date, last password change, password age, etc.

If a password field has `*` or `!`, user cannot connect to system using **password authentication**.
