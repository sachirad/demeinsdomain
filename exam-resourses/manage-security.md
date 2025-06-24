---
icon: shield-check
---

# Manage Security

### Practice Questions: "Manage Security" (RHCSA v9)

Below are exam-style questions covering every subtopic in both "Manage security" and "Manage containers" as required by RHCSA v9.

***

## <mark style="color:green;">Questions</mark>

**Configure firewall settings using firewall-cmd/firewalld**

* List all active firewall zones and their associated interfaces.
* Add the HTTP and HTTPS services to the public zone permanently and reload the firewall to apply changes.
* Open TCP port 8080 in the public zone and make the change permanent.
* Remove the SSH service from the public zone and verify its removal.
* Add a rich rule to block all incoming traffic from the IP address 192.168.1.100 permanently.
* Display all enabled services and open ports for the public zone[^1].

**Manage default file permissions**

* Set the default umask for all users to 027 system-wide.
* Verify your current shell session's umask.
* Change a file's permissions so the owner has rw, group has r, others have no access.

**Configure key-based authentication for SSH**

* Generate an SSH key pair for user `student` with no passphrase.
* Copy the public key to `node2.example.com` for passwordless SSH login.
* Configure the SSH server to allow only key-based authentication and disable password authentication.

**Set enforcing and permissive modes for SELinux**

* Check the current SELinux mode.
* Temporarily set SELinux to permissive mode.
* Permanently set SELinux to enforcing mode and reboot to apply.

**List and identify SELinux file and process context**

* Display the SELinux context of `/var/www/html` and all its contents.
* List SELinux process contexts for all running processes.

**Restore default file contexts**

* Restore the default SELinux context for `/var/www/html` recursively.
* After moving a file to a new directory, restore its SELinux context.

**Manage SELinux port labels**

* List all SELinux port types and their assigned ports.
* Add TCP port 8081 to the `http_port_t` type.
* Remove the custom port label for TCP port 8081.

**Use boolean settings to modify system SELinux settings**

* Enable the SELinux boolean `httpd_can_network_connect` and make it persistent.
* Temporarily disable the boolean `allow_ftpd_anon_write`.

**Diagnose and address routine SELinux policy violations**

* Use `ausearch` or `journalctl` to find SELinux denials related to the HTTPD service.
* Generate a custom SELinux policy module to allow a denied action and load it.
* Use `setenforce 0` to troubleshoot and then re-enable enforcing mode.

***

## <mark style="color:yellow;">Answers</mark>

**Configure firewall settings using firewall-cmd/firewalld**

* List all active firewall zones and their associated interfaces.
* Add the HTTP and HTTPS services to the public zone permanently and reload the firewall to apply changes.
* Open TCP port 8080 in the public zone and make the change permanent.
* Remove the SSH service from the public zone and verify its removal.
* Add a rich rule to block all incoming traffic from the IP address 192.168.1.100 permanently.
* Display all enabled services and open ports for the public zone[^1].

**Manage default file permissions**

* Set the default umask for all users to 027 system-wide.
* Verify your current shell session's umask.
* Change a file's permissions so the owner has rw, group has r, others have no access.

**Configure key-based authentication for SSH**

* Generate an SSH key pair for user `student` with no passphrase.
* Copy the public key to `node2.example.com` for passwordless SSH login.
* Configure the SSH server to allow only key-based authentication and disable password authentication.

**Set enforcing and permissive modes for SELinux**

* Check the current SELinux mode.
* Temporarily set SELinux to permissive mode.
* Permanently set SELinux to enforcing mode and reboot to apply.

**List and identify SELinux file and process context**

* Display the SELinux context of `/var/www/html` and all its contents.
* List SELinux process contexts for all running processes.

**Restore default file contexts**

* Restore the default SELinux context for `/var/www/html` recursively.
* After moving a file to a new directory, restore its SELinux context.

**Manage SELinux port labels**

* List all SELinux port types and their assigned ports.
* Add TCP port 8081 to the `http_port_t` type.
* Remove the custom port label for TCP port 8081.

**Use boolean settings to modify system SELinux settings**

* Enable the SELinux boolean `httpd_can_network_connect` and make it persistent.
* Temporarily disable the boolean `allow_ftpd_anon_write`.

**Diagnose and address routine SELinux policy violations**

* Use `ausearch` or `journalctl` to find SELinux denials related to the HTTPD service.
* Generate a custom SELinux policy module to allow a denied action and load it.
* Use `setenforce 0` to troubleshoot and then re-enable enforcing mode.



⁂

[^1]: https://docs.redhat.com/en/documentation/red\_hat\_enterprise\_linux/9/html/configuring\_firewalls\_and\_packet\_filters/using-and-configuring-firewalld\_firewall-packet-filters
