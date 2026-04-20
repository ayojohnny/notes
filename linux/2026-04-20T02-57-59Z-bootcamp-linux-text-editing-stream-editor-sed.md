# Linux | Text Editing - Stream Editor (sed)

`sed`
- stream editor for filtering and transforming text
- transforms text then prints to standard out
- modifies text if `-i` option is used

Use cases:
- modify config file across multiples systems
- replace text automatically (i.e. scriptable)


Given a text file called `foobar.txt` with contents:

"Welcome to Ubuntu
Ubuntu Server rocks

Bye!"


```bash
# Replace first occurrence of Ubuntu w/ Debian.
# Does not modify file.
sed 's/Ubuntu/Debian/' foobar.txt

# Replace all occurrences of Ubuntu w/ Debian.
# Does not modify file.
sed 's/Ubuntu/Debian/g' foobar.txt

# Replace all occurrences of Ubuntu w/ Debian.
# Modifies file contents.
sed -i 's/Ubuntu/Debian/g' foobar.txt

# Create a backup file (.bak) of original content.
# Replace all occurrences of Ubuntu w/ Debian.
# Modifies file contents.
sed -i.bak 's/Ubuntu/Debian/g' foobar.txt
```

Use Case: Editing SSH Daemon Config
```bash
# Check if `root` can log in to system.
grep PermitRootLogin /etc/ssh/sshd_config

# output: #PermitRootLogin yes

# Disable root login.
sudo sed -i 's/^#PermitRootLogin.*/PermitRootLogin no/' /etc/ssh/sshd_config

# Check again.
grep PermitRootLogin /etc/ssh/sshd_config

# output: PermitRootLogin no

# Disable password authentication
grep PasswordAuthentiaction /etc/ssh/sshd_config
# output: #PasswordAuthentication yes

sudo sed -i 's/#PasswordAuthentication.*/PasswordAuthentication no/' /etc/ssh/sshd_config

# Apeend this line to file if it does not exist.
sudo sed -i $a PasswordAuthentication no' /etc/ssh/sshd_config
```
