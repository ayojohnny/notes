# Linux Bootcamp | Filesystem Hierarchy Standard (FHS)

Filesystem Hierarchy Standard 
- maintained by Linux foundation
- documents the Linux file system 

Directory `/bin`
- binaries or user executable files which are available to all users

Directory `/sbin`
- contains applications that only the superuser will need (hence the `s`)
- these programs are often used for system administration (i.e. `ifconfig`, etc. )

Directory `/boot`
- contains files required for starting system

Directory `/home`
- users' home directories
- each user gets own directory

Directory `/root`
- contains home directory for `root` user

Directory `/dev`
- contains device files
- **not** devices drivers - files that represent devices attached

Directory `/etc`
- contains system-wide configuration files

Directory `/lib`
- contains shared library files used by different applications
- usually modified by the package manager

Directory `/media`
- external storage mounted here

Directory `/mnt`
- alternative mount point
- originally used for cdroms and floppy disks

Directory `/tmp`
- temporary files usually saved by running applications
- non-privileged users can store files here
- files here can be deleted any time without notice

Directory `/proc`
- hardware related information (cpu, memory, etc.)
- generated at runtime or at startup

Directory `/sys`
- information about devices, drivers, and some kernel features
- not used directly

Directory `/srv`
- contains data for servers
- not used directly

Directory `/run`
- new
- temporary, contents loaded in RAM
- used only by processes

Directory `/usr`
- initial place for home directories
- in modern systems, contains binaries and shared libs for users

Directory `/var`
- variable length files (i.e. logs, events, etc.)
