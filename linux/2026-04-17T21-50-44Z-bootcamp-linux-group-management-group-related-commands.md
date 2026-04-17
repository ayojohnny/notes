# Linux | Group Managment - Create Group

`groupadd`: native command for adding groups
`groupmod`: change group information
`groupdel`: delete a group

```bash
# Create `finance` group
sudo groupadd finance

tail -3 /etc/group
# foo:x:1001:
# bar:x:1002:
# finance:x:1003:


# Add bob to finance.
sudo usermod -aG finance bob

sudo groupmod -n finace developers

sudo groupdel finance
```

It is not possible to remove the primary group of a user without first
deleting the associated user. For example, cannot delete `bob` group without first
deleting `bob` user.

