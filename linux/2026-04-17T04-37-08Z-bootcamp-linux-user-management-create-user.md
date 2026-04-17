# Linux | User Management - Create User

Root privileges are required to create, change, or delete an account.

`useradd`
- native way to add users

`passwd`:
- command for setting a user's password

`/etc/default/useradd`
- file containing default options for the useradd command
- defaults for useradd will vary by distribution.

`/etc/logins.def`
- contain defaults for the shadow password file (expiry, policy, etc.)

```bash
# sudo useradd <username>
sudo useradd johndoe

# Set user password to allow logins.
sudo passwd johndoe

# New password: <enterPassword>
# Retype new password: <enterPassword>
# passwd : password updated successfully
```

```bash
# create user with common information
sudo useradd -m -d /home/james -c "Comment" -s /bin/bash -G sudo,adm,mail <userName>
```

```bash
# Create <username>, set to expire at target YYYY-MM-DD
sudo useradd -e YYYY-MM-DD <username>
```

`chage`:
- command to work with account policies, expiration, etc.
