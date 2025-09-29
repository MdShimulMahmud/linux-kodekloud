# Level 2

## Task List

| No. | Task Description                                                                | Solution                                               |
| --- | ------------------------------------------------------------------------------- | ------------------------------------------------------ |
| 1   | [Create a Cron Job](#task-1-create-a-cron-job)                                  | [Solution](#task-1-create-a-cron-job)                  |
| 2   | [Linux Banner](#task-2-linux-banner)                                            | [Solution](#task-2-linux-banner)                       |
| 3   | [Linux Collaborative Directories](#task-3-linux-collaborative-directories)      | [Solution](#task-3-linux-collaborative-directories)    |
| 4   | [Linux String Substitute (sed)](#task-4-linux-string-substitute-sed)            | [Solution](#task-4-linux-string-substitute-sed)        |
| 5   | [Linux SSH Authentication](#task-5-linux-ssh-authentication)                    | [Solution](#task-5-linux-ssh-authentication)           |
| 6   | [Linux Find Command](#task-6-linux-find-command)                                | [Solution](#task-6-linux-find-command)                 |
| 7   | [Install a package](#task-7-install-a-package)                                  | [Solution](#task-7-install-a-package)                  |
| 8   | [Install Ansible](#task-8-install-ansible)                                      | [Solution](#task-8-install-ansible)                    |
| 9   | [Configure Local Yum repos](#task-9-configure-local-yum-repos)                  | [Solution](#task-9-configure-local-yum-repos)          |
| 10  | [Linux Services](#task-10-linux-services)                                       | [Solution](#task-10-linux-services)                    |
| 11  | [Linux Configure sudo](#task-11-linux-configure-sudo)                           | [Solution](#task-11-linux-configure-sudo)              |
| 12  | [DNS Troubleshooting](#task-12-dns-troubleshooting)                             | [Solution](#task-12-dns-troubleshooting)               |
| 13  | [Linux Firewalld Setup](#task-13-linux-firewalld-setup)                         | [Solution](#task-13-linux-firewalld-setup)             |
| 14  | [Linux Postfix Mail Server](#task-14-linux-postfix-mail-server)                 | [Solution](#task-14-linux-postfix-mail-server)         |
| 15  | [Linux Postfix Troubleshooting](#task-15-linux-postfix-troubleshooting)         | [Solution](#task-15-linux-postfix-troubleshooting)     |
| 16  | [Install and Configure HaProxy LBR](#task-16-install-and-configure-haproxy-lbr) | [Solution](#task-16-install-and-configure-haproxy-lbr) |
| 17  | [Haproxy LBR Troubleshooting](#task-17-haproxy-lbr-troubleshooting)             | [Solution](#task-17-haproxy-lbr-troubleshooting)       |
| 18  | [MariaDB Troubleshooting](#task-18-mariadb-troubleshooting)                     | [Solution](#task-18-mariadb-troubleshooting)           |
| 19  | [Linux Bash Scripts](#task-19-linux-bash-scripts)                               | [Solution](#task-19-linux-bash-scripts)                |
| 20  | [Add Response Headers in Apache](#task-20-add-response-headers-in-apache)       | [Solution](#task-20-add-response-headers-in-apache)    |
| 21  | [Apache Troubleshooting](#task-21-apache-troubleshooting)                       | [Solution](#task-21-apache-troubleshooting)            |
| 22  | [Linux GPG Encryption](#task-22-linux-gpg-encryption)                           | [Solution](#task-22-linux-gpg-encryption)              |
| 23  | [Linux LogRotate](#task-23-linux-logrotate)                                     | [Solution](#task-23-linux-logrotate)                   |
| 24  | [Application Security](#task-24-application-security)                           | [Solution](#task-24-application-security)              |


----------------------------------------------------------------------------

## Task 1: Create a Cron Job

```shell
sudo yum update -y
sudo yum install cronie -e
sudo systemctl start crond
sudo systemctl status crond
sudo crontab -e
# Add the following line to run the script 
*/5 * * * * echo hello > /tmp/cron_text
sudo crontab -l
```
This commands will create a cron job that runs every 5 minutes and writes "hello" to the file /tmp/cron_text.

## Task 2: Linux Banner

```shell
# Do this for all application servers and db server
scp -r /home/thor/nautilus_banner tony@stapp01:/tmp
ssh tony@stapp01
sudo mv /tmp/nautilus_banner /etc/motd
cat /etc/motd
exit
```
This commands will copy the nautilus_banner file to the /etc/motd file on the stapp01 server, which is displayed when a user logs in.

## Task 3: Linux Collaborative Directories

```shell
sudo mkdir -p /devops/data
sudo chown :devops /devops/data
sudo chmod 770 /devops/data
# Ensure new files inherit the group ownership
sudo chmod g+s /devops/data
ls -ld /devops/data
```
This commands will create the /devops/data directory, set the group ownership to devops, and set the permissions to allow read, write, and execute for the owner and group, but no permissions for others.

## Task 4: Linux String Substitute (sed)

```shell
grep -v 'copyright' /home/BSD.txt > /home/BSD_DELETE.txt
cat /home/BSD_DELETE.txt
sed 's/\bfrom\b/for/g' /home/BSD.txt > /home/BSD_REPLACE.txt
cat /home/BSD_REPLACE.txt
```
This commands will create a new file BSD_DELETE.txt that contains all lines from BSD.txt except those containing the word "copyright". It will also create a new file BSD_REPLACE.txt that replaces all occurrences of the word "from" with "for".

