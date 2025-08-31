# Solution of Level 1

## Task 1: Custom Apache User Setup

```shell
sudo useradd -u 1567 -d /var/www/john john

sudo mkdir -p /var/www/john

sudo chown john:john /var/www/john

id john
```

This command creates a new user `john` with the specified UID and home directory, creates the directory `/var/www/john`, changes its ownership to `john`, and finally displays the user information for `john`.


## Task 2: Group Creation and User Assignment

```shell    
sudo groupadd nautilus_team_users
sudo adduser -g nautilus_team_users kano
id kano
```
This command creates a new group `nautilus_team_users`, adds the user `kano` to this group, and then displays the user information for `kano` to verify the group assignment.