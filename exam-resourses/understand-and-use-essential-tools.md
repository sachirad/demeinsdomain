---
icon: screwdriver-wrench
---

# Understand and Use Essential Tools

### Practice Questions: "Understand and Use Essential Tools" (RHCSA v9)

Below are hands-on, exam-style questions covering every subtopic you listed. These are modeled on real-world RHCSA exam tasks and community practice labs[^1].

***

**Access a shell prompt and issue commands with correct syntax**

* Log in as the user `student` and open a Bash shell. Display your current working directory and list all files, including hidden ones, with detailed information.

**Use input-output redirection (>, >>, |, 2>, etc.)**

* Redirect the output of `ls /etc` to a file called `etc_list.txt`.
* Append the output of `date` to `etc_list.txt`.
* Redirect any errors from the command `ls /nonexistent` to a file called `error.log`.
* Combine standard output and standard error from `cat /etc/passwd /nonexistent` into a file named `combined.log`.

**Use grep and regular expressions to analyze text**

* Find all lines containing the word "root" (case-insensitive) in `/etc/passwd`.
* Display all files in `/etc` that end with `.conf` using a command pipeline.
* Using a regular expression, find all lines in `/var/log/messages` that start with a number[^1].

**Access remote systems using SSH**

* Use SSH to connect from your current system to `node2.example.com` as user `student`.
* Copy the file `/etc/hosts` to your home directory on `node2.example.com` using a single command[^2].

**Log in and switch users in multiuser targets**

* Check the current default system target.
* Change the default system target to `multi-user.target` and reboot the system.
* Switch from your current user to the root account using the appropriate command[^3].

**Archive, compress, unpack, and uncompress files using tar, gzip, and bzip2**

* In your home directory, create a gzip-compressed tar archive of the `/etc` directory named `etc.tar.gz`.
* Create a bzip2-compressed tar archive of the `/var/log` directory named `log.tar.bz2`.
* List the contents of both archives.
* Extract both archives into a directory called `extracted` in your home directory[^4].

**Create and edit text files**

* Create a new file called `notes.txt` in your home directory and add the text "RHCSA Practice".
* Open `notes.txt` with `vim`, add another line, and save the file[^5].

**Create, delete, copy, and move files and directories**

* Create a directory called `practice` in your home directory.
* Copy `notes.txt` into `practice/`.
* Move `notes.txt` from your home directory into `practice/`.
* Delete the `practice` directory and its contents.

**Create hard and soft links**

* Create a hard link to `/etc/hosts` named `hosts.hard` in your home directory.
* Create a symbolic (soft) link to `/etc/hosts` named `hosts.soft` in your home directory.

**List, set, and change standard ugo/rwx permissions**

* Change the permissions of `notes.txt` so that only the owner can read and write it.
* Set the permissions of `practice/` so that everyone can read, write, and execute files in it.
* Use `ls -l` to display the permissions of both files and directories[^1].

**Locate, read, and use system documentation including man, info, and files in /usr/share/doc**

* Use the `man` command to find out how to use the `tar` command.
* Use the `info` command to learn about the `grep` command.
* Find and read the README file for the `bash` package in `/usr/share/doc`.

***

#### Tips

* Practice each task on a real or virtual RHEL 9 system.
* Use only the command line (no graphical tools).
* Ensure changes persist after reboot where relevant.

These questions will help you cover all essential tools required by the RHCSA v9 exam[^1].

⁂

[^1]: https://alldrops.info/posts/linux-drops/2021-09-15\_rhcsa-8-understand-and-use-essential-tools/

[^2]: https://www.youtube.com/watch?v=5lRAdO4kYVc

[^3]: https://linuxconfig.org/log-in-and-switch-users-in-multiuser-targets-rhcsa-objective-preparation

[^4]: https://dev.to/labex/create-and-extract-tar-archivesrhcsa-exam-questions-ed0

[^5]: https://www.pearsonitcertification.com/articles/article.aspx?p=3178909
