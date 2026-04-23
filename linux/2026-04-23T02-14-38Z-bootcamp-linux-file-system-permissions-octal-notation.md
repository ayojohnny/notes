# Linux | Filesystem - File Persmissions - Octal Notation

Octal notation:
- method of changing file permissions
- base-8 number (3-4 digits). Digits range from 0-7
    - 0 can be omitted (i.e. 0755 = 755, 0644 = 644)

Octal Number    | Permissions Granted
--              | --
7               | read + write + execute
6               | read + write
5               | read + execute
4               | read
3               | write + execute
2               | write
1               | execute
0               | no permissions

The permissions are a **sum of the values**.

Given a symbolic permission `rw-rw-r--`, broken down to:

User:   6 -> 4 (read) + 2 (write) + 0 (no permission)
Group:  6 -> 4 (read) + 2 (write) + 0 (no permission)
Other:  4 -> 4 (read) + 0 (no permission) + 0 (no permisson)

resulting command: `chmod 664 <someFile>`

