---
icon: ubuntu
---

# Operate Running Systems

### Practice Questions: "Operate Running Systems" (RHCSA v9)

These questions are tailored to the RHCSA v9 exam objectives and reflect real-world exam scenarios, including tasks similar to those found in past exams.

***

## <mark style="color:green;">Questions</mark>

**Boot, reboot, and shut down a system normally**

* Reboot the system immediately using the command line.
* Shut down the system after a delay of 2 minutes and display a custom message to logged-in users.
* Power off the system at a specific time (e.g., 23:30) using a single command.

**Boot systems into different targets manually**

* Change the current system to `multi-user.target` without rebooting.
* Set the default target to `graphical.target` so the system boots into GUI mode by default.
* During boot, interrupt the boot process and modify it so the system starts in `rescue.target` for troubleshooting.

**Interrupt the boot process in order to gain access to a system**

* Interrupt the boot process and reset the root password by editing kernel parameters at boot time (e.g., using GRUB).

**Identify CPU/memory intensive processes and kill processes**

* List the top five processes consuming the most CPU on your system.
* Kill a process with a specific PID using the appropriate command.
* Use `top` or `ps` to find and terminate a process called `stress`.

**Adjust process scheduling**

* Start a process (`sleep 1000`) with a lower priority (higher nice value).
* Change the scheduling priority of a running process to a higher priority (lower nice value).
* Use `chrt` to set a real-time scheduling policy for a process.

**Manage tuning profiles**

* List all available tuning profiles on the system.
* Apply the `throughput-performance` profile using the correct command.
* Verify which tuning profile is currently active.

**Locate and interpret system log files and journals**

* Use `journalctl` to display all system logs from today.
* Find and display all log entries in `/var/log/messages` that mention "error".
* Export all log messages containing "ACPI" from `~/logs/messages` to a file called `~/acpi_logs`.

**Preserve system journals**

* Make systemd journals persistent across reboots.
* Limit the maximum size of persistent journals to 50MB and apply the change.

**Start, stop, and check the status of network services**

* Start and enable the `sshd` service.
* Stop the `httpd` service and check its status.
* Verify if the `firewalld` service is running and restart it if necessary.

**Securely transfer files between systems**

* Use `scp` to copy a file named `backup.tar.gz` from your current system to the `/tmp` directory on `node2.example.com` as user `student`.
* Use `rsync` to synchronize the `/home/student/docs` directory to another system at `node2.example.com` under the same path.

***

## <mark style="color:red;">Answers</mark>

**Boot, reboot, and shut down a system normally**

* Reboot the system immediately using the command line.
* Shut down the system after a delay of 2 minutes and display a custom message to logged-in users.
* Power off the system at a specific time (e.g., 23:30) using a single command.

**Boot systems into different targets manually**

* Change the current system to `multi-user.target` without rebooting.
* Set the default target to `graphical.target` so the system boots into GUI mode by default.
* During boot, interrupt the boot process and modify it so the system starts in `rescue.target` for troubleshooting.

**Interrupt the boot process in order to gain access to a system**

* Interrupt the boot process and reset the root password by editing kernel parameters at boot time (e.g., using GRUB).

**Identify CPU/memory intensive processes and kill processes**

* List the top five processes consuming the most CPU on your system.
* Kill a process with a specific PID using the appropriate command.
* Use `top` or `ps` to find and terminate a process called `stress`.

**Adjust process scheduling**

* Start a process (`sleep 1000`) with a lower priority (higher nice value).
* Change the scheduling priority of a running process to a higher priority (lower nice value).
* Use `chrt` to set a real-time scheduling policy for a process.

**Manage tuning profiles**

* List all available tuning profiles on the system.
* Apply the `throughput-performance` profile using the correct command.
* Verify which tuning profile is currently active.

**Locate and interpret system log files and journals**

* Use `journalctl` to display all system logs from today.
* Find and display all log entries in `/var/log/messages` that mention "error".
* Export all log messages containing "ACPI" from `~/logs/messages` to a file called `~/acpi_logs`.

**Preserve system journals**

* Make systemd journals persistent across reboots.
* Limit the maximum size of persistent journals to 50MB and apply the change.

**Start, stop, and check the status of network services**

* Start and enable the `sshd` service.
* Stop the `httpd` service and check its status.
* Verify if the `firewalld` service is running and restart it if necessary.

**Securely transfer files between systems**

* Use `scp` to copy a file named `backup.tar.gz` from your current system to the `/tmp` directory on `node2.example.com` as user `student`.
* Use `rsync` to synchronize the `/home/student/docs` directory to another system at `node2.example.com` under the same path.



⁂
