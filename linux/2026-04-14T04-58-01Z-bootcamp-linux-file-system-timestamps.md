# Linux | Filesystem - Timestamps


Every file on Linux has 3 timestamps - `atime`, `mtime`, and `ctime`

`atime` (access time)
- last time the file was read (i.e. `ls -lu`, etc.)
- does not matter if contents or metadata was changed 

`mtime` (modified time)
- last time the contents of the file was modified (i.e. `ls -l`, `ls -lt`)

`ctime` (changed time)
- last time some metadata related to the file was changed (`ls -lc`)
- some triggers: changing file permissions or owner

Linux Timestamps:
- hold integer value instead of a date and time
- the value = Linux Epoch
    - when using dates, Linux translates the total seconds into a date and time

Linux Epoch: number of seconds since unique epoch on Jan 1st, 1970 UTC

`stat`
- command that allows viewing timestamps

`ls -l --full-time` show full timestamp

`touch`
- command that modifies the `ctime`
- creates files if the file doesn't exist

`touch -a <file>`
- change only the access time

`toch -m  -t 201812301530.45 <file>`
- set modified time on a file

`ls -lt`
- sort files by modification `mtime`

`ls -ltu`
- sort files by access time

`ls -lu`
- sort files by name and show access time

`ls -lur` or `ls -lu --revserse`
- sort files by name, show access time, and reverse listing
