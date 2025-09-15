
# Solution of Level 1


## Task List

| No. | Task Description                                                                                     | Solution                                                         |
| --- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| 1   | [Custom Apache User Setup](#task-1-custom-apache-user-setup)                                         | [Solution](#task-1-custom-apache-user-setup)                     |
| 2   | [Group Creation and User Assignment](#task-2-group-creation-and-user-assignment)                     | [Solution](#task-2-group-creation-and-user-assignment)           |
| 3   | [Linux User Setup with Non-Interactive Shell](#task-3-linux-user-setup-with-non-interactive-shell)   | [Solution](#task-3-linux-user-setup-with-non-interactive-shell)  |
| 4   | [Service User Creation without Home Directory](#task-4-service-user-creation-without-home-directory) | [Solution](#task-4-service-user-creation-without-home-directory) |
| 5   | [Temporary User Setup with Expiry](#task-5-temporary-user-setup-with-expiry)                         | [Solution](#task-5-temporary-user-setup-with-expiry)             |
| 6   | [Linux User Data Transfer](#task-6-linux-user-data-transfer)                                         | [Solution](#task-6-linux-user-data-transfer)                     |
| 7   | [Secure Root SSH Access](#task-7-secure-root-ssh-access)                                             | [Solution](#task-7-secure-root-ssh-access)                       |
| 8   | [Data Backup for Developer](#task-8-data-backup-for-developer)                                       | [Solution](#task-8-data-backup-for-developer)                    |
| 9   | [Script Execution Permissions](#task-9-script-execution-permissions)                                 | [Solution](#task-9-script-execution-permissions)                 |
| 10  | [File Permission Correction](#task-10-file-permission-correction)                                    | [Solution](#task-10-file-permission-correction)                  |
| 11  | [String Replacement](#task-11-string-replacement)                                                    | [Solution](#task-11-string-replacement)                          |
| 12  | [Secure Data Transfer](#task-12-secure-data-transfer)                                                | [Solution](#task-12-secure-data-transfer)                        |
| 13  | [Restrict Cron Access](#task-13-restrict-cron-access)                                                | [Solution](#task-13-restrict-cron-access)                        |
| 14  | [Default GUI Boot Configuration](#task-14-default-gui-boot-configuration)                            | [Solution](#task-14-default-gui-boot-configuration)              |
| 15  | [Timezone Alignment](#task-15-timezone-alignment)                                                    | [Solution](#task-15-timezone-alignment)                          |
| 16  | [Firewall Configuration](#task-16-firewall-configuration)                                            | [Solution](#task-16-firewall-configuration)                      |
| 17  | [Process Limit Adjustment](#task-17-process-limit-adjustment)                                        | [Solution](#task-17-process-limit-adjustment)                    |
| 18  | [SElinux Installation and Configuration](#task-18-selinux-installation-and-configuration)            | [Solution](#task-18-selinux-installation-and-configuration)      |


--------------------------------------------------
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


## Task 3: Linux User Setup with Non-Interactive Shell

```shell
sudo useradd -s /sbin/nologin james
# Or run this
sudo useradd -s /bin/false james

id james

# Check the shell assigned to the user
cat /etc/passwd | grep james
```
This command creates a new user `james` with a non-interactive shell and a specified home directory, and then displays the user information for `james` to verify the setup.

## Task 4: Service User Creation without Home Directory

```shell    
sudo useradd -M jim
id jim
``` 
This command creates a new user `jim` without a home directory and then displays the user information for `jim` to verify the setup.

## Task 5: Temporary User Setup with Expiry

```shell    
sudo useradd -e 2024-12-31 rose
id rose
```
This command creates a new user `rose` with an expiration date of December 31, 2024, and then displays the user information for `rose` to verify the setup.


## Task 6: Linux User Data Transfer

```shell    
find /home/usersdata -type f -user rose

find /home/usersdata -type f -user rose -exec cp --parents {} /beta \;
```
This command finds all files owned by the user `rose` in the `/home/usersdata` directory and copies them to the `/beta` directory while preserving their directory structure.


## Task 7: Secure Root SSH Access

```shell   
sudo sed -i 's/^#\?PermitRootLogin .*/PermitRootLogin no/' /etc/ssh/sshd_config
sudo systemctl restart sshd
```
This command modifies the SSH configuration to disable root login and then restarts the SSH service to apply the changes.

## Task 8: Data Backup for Developer

```shell    
sudo tar -czf /tmp/javed.tar.gz /data/javed
sudo mv /tmp/javed.tar.gz /home/
ls -l /home/javed.tar.gz

```
This command creates a tar archive of the `/data/javed` directory and saves it as `/home/javed.tar.gz`. 

## Task 9: Script Execution Permissions

```shell
sudo chmod +x /tmp/xfusioncorp.sh
ls -l /tmp/xfusioncorp.sh
```
This command adds execute permissions to the `xfusioncorp.sh` script and then lists the file details to verify the permission change.

## Task 10: File Permission Correction

```shell
sudo chown root:root /etc/resolv.conf
sudo chmod 644 /etc/resolv.conf
sudo setfacl -x u:yousuf /etc/resolv.conf
sudo setfacl -m u:yousuf:--- /etc/resolv.conf
sudo setfacl -m u:jerome:r-- /etc/resolv.conf
getfacl /etc/resolv.conf
ls -l /etc/resolv.conf
```
This command corrects the ownership and permissions of the `/etc/resolv.conf` file, removes any existing ACL for user `yousuf`, adds a read-only ACL for user `jerome`, and then displays the ACL and file details to verify the changes.

## Task 11: String Replacement

```shell
sudo sed -i 's/About/Torpedo/g' /root/nautilus.xml
cat /tmp/nautilus.xml | grep Torpedo | wc -l
```
This command replaces all occurrences of the string "About" with "Torpedo" in the `/root/nautilus.xml` file and then counts the number of lines containing the string "Torpedo" to verify the replacement.

## Task 12: Secure Data Transfer

```shell
scp /tmp/nautilus.txt.gpg steve@stapp02:/home/appdata
ssh steve@stapp02
ls -la /home/appdata/
```
This command securely copies the `nautilus.txt.gpg` file to the `/home/appdata` directory on the remote server `stapp02` using SCP, then connects to the remote server via SSH and lists the contents of the `/home/appdata/` directory to verify the transfer.