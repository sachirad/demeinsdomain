# RHCSA EX200 Exam Scenario

## Scenario: Linux Administrator at XYZ Corp

You have been hired as a Linux Administrator at XYZ Corp. Your first task is to set up and configure a Red Hat Enterprise Linux (RHEL) server according to the company's security and operational guidelines.

***

## Task 1: User & Group Management

* Create a new group named `webadmins`.
* Create two new users: `alice` and `bob`, and add them to the `webadmins` group.
* Set the password for both users as `RedHat123!`.
* Ensure that `alice` has a home directory at `/home/alice` and a default shell of `/bin/bash`.
* Lock the `bob` user account.

***

## Task 2: File Permissions & ACLs

* Create a directory `/var/www/project` owned by `root:webadmins` with `775` permissions.
* Allow only `alice` to read and write files inside this directory using ACLs.
* Create a file `/var/www/project/config.txt` and set permissions so that only `root` can modify it, but all `webadmins` can read it.

***

## Task 3: Networking

* Set a static IP address `192.168.50.100/24` on interface `ens160` with a gateway of `192.168.50.1`.
* Configure the DNS resolver to use `8.8.8.8` and `8.8.4.4`.
* Restart the network service and verify connectivity with `ping 8.8.8.8`.

***

## Task 4: Firewall & Security

* Allow only HTTP (port `80`) and SSH (port `22`) traffic in the firewall and make the rule persistent.
* Ensure that the firewall is enabled and running at startup.
* List all active firewall rules.

***

## Task 5: SELinux

* Verify the current SELinux status.
* Set SELinux to permissive mode permanently.
* Restore SELinux contexts on `/var/www/project/` if required.

***

## Task 6: Storage & LVM

* Create a new logical volume named `webdata` of `2GB` on `/dev/vdb`, under a volume group `webvg`.
* Format the logical volume with `XFS` and mount it permanently at `/mnt/webdata`.
* Ensure the mount is persistent after reboot.

***

## Task 7: Process & Service Management

* Install and enable the `httpd` service.
* Ensure that `httpd` starts automatically on boot.
* Restart the `httpd` service and check its status.

***

## Task 8: Scheduled Jobs (Cron & Systemd Timers)

* Create a cron job for `alice` that runs `/home/alice/backup.sh` at `3 AM` daily.
* Create a systemd timer that runs a script `/opt/cleanlogs.sh` every Sunday at midnight.

***

## Task 9: Bash Scripting

Write a Bash script named `disk_alert.sh` that:

* Checks if disk usage on `/` is above `80%`.
* If yes, logs an alert message to `/var/log/disk_alert.log`.
* Make the script executable and schedule it using cron to run every `30 minutes`.

***

## Task 10: Troubleshooting & Logs

* Find the last `10` failed login attempts from the authentication logs.
* Check if any service has crashed in the last `24 hours` using system logs.
* Display all running processes owned by `alice`.

***

## Bonus: Commands & Answers

If you want the solutions, let me know, and I'll provide the exact commands for each task! 🚀🔥
