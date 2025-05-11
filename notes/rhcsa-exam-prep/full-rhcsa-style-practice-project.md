# Full RHCSA Style Practice Project

### Full RHCSA-Style Practice Project

This project simulates a real-world scenario and covers every major competency listed in your image, similar to the RHCSA exam. Complete all tasks **on a fresh CentOS/RHEL 9 virtual machine** (or equivalent), using only the CLI unless otherwise specified.

***

#### **Scenario**

You are the new Linux administrator for a company. Your task is to set up, secure, and maintain a server to company standards. Complete the following tasks step by step.

***

#### **Project Tasks**

**1. Essential Tools and File Operations**

* Create a user account called `sysadmin` and set its password to expire in 10 days.
* Log in as `sysadmin` in a new terminal session.
* Create directories: `/project/docs`, `/project/scripts`, and `/project/archive`.
* Create a text file `/project/docs/readme.txt` with the content "Project Documentation".
* Create a hard link and a symbolic link to `readme.txt` in `/project/archive`.
* Set permissions so only members of a new group `projgrp` can write to `/project/docs`.
* Add `sysadmin` to `projgrp`.
* Use `find` to locate all `.txt` files in `/project` and redirect the output to `/project/docs/files.txt`.
* Use `grep` to find the word "Project" in all `.txt` files under `/project/docs`.
* Archive `/project` using `tar` and compress it with `gzip`. Store the archive in `/tmp`.

**2. Shell Scripting**

* Write a script `/project/scripts/backup.sh` that:
  * Archives `/project/docs` to `/project/archive/backup.tar.gz`
  * Logs the date and success/failure to `/project/archive/backup.log`
* Make the script executable and schedule it to run daily at 2:00 AM using `cron`.

**3. System and Service Management**

* Reboot the system and verify it boots into the default target.
* Change the default system target to `multi-user.target`.
* Start and enable the `sshd` and `firewalld` services so they persist across reboots.
* Use `systemctl` to check the status of both services.
* Adjust the system `hostname` to `projecthost`.
* Use `journalctl` and `dmesg` to view logs for the last boot.

**4. Storage and File System Management**

* Add a new virtual disk to your VM (or create a new file-backed loop device).
* Partition the disk with a single partition using `fdisk` or `parted`.
* Create a physical volume, volume group (`projvg`), and logical volume (`projlv`) using LVM.
* Format the logical volume with `ext4` and mount it at `/mnt/projectdata`.
* Configure `/etc/fstab` to mount it at boot using its UUID.
* Extend the logical volume by 500MB and resize the filesystem.

**5. File Sharing and Collaboration**

* Install and configure NFS to export `/mnt/projectdata` to the local network.
* On a second VM or using localhost, mount the NFS share at `/mnt/nfsproject`.
* Create a set-GID directory `/mnt/projectdata/team` so all files created inside inherit the group.

**6. Networking**

* Configure a static IPv4 address for your main network interface.
* Set up `/etc/hosts` to resolve `projecthost` to its IP.
* Restrict access using `firewall-cmd` to allow only SSH and NFS.
* Test connectivity with `ping`, `traceroute`, and `nc`.

**7. Security**

* Configure SSH key-based authentication for `sysadmin`.
* Disable password authentication for SSH.
* Set SELinux to enforcing mode and verify.
* Use `ls -Z` and `ps -eZ` to inspect SELinux contexts.
* Restore SELinux contexts on `/mnt/projectdata` if needed.
* Use `firewall-cmd` to open and close ports as required.

**8. Containers**

* Install Podman.
* Pull the latest `nginx` image.
* Run a container named `webserver` with:
  * Port 8080 mapped to container port 80
  * Persistent storage from `/mnt/projectdata/web` to `/usr/share/nginx/html`
* Configure the container to start automatically as a systemd service.

***

#### **Submission**

* For each task, document:
  * The exact commands used
  * Any configuration files modified (with before/after snippets)
  * Screenshots or output confirming success

***

This project will comprehensively test your ability to perform all the tasks expected in the RHCSA exam, mimicking real-world administrator duties. Good luck!

⁂
