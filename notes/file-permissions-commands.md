# File Permissions Commands

## **Change File Permissions (chmod)**

The `chmod` command is used to change the permissions of a file or directory. Permissions are represented using a three-digit octal number or symbolic notation.

### **Octal Notation**

Each digit represents the permissions for the user (owner), group, and others:

* **Read (r)** = 4
* **Write (w)** = 2
* **Execute (x)** = 1

Examples:

* `755` = Full permissions for the owner, read and execute for group and others.
* `644` = Read and write for the owner, read-only for group and others.

#### **Usage**

```bash
chmod 755 file_name
chmod 644 file_name
```

### **Symbolic Notation**

Use `u` (user), `g` (group), `o` (others), and `a` (all):

* `+` to add permissions.
* `-` to remove permissions.
* `=` to set exact permissions.

#### **Usage**

```bash
chmod u+x file_name    # Add execute permission for user
chmod g-w file_name    # Remove write permission for group
chmod o=r file_name    # Set read-only for others
```

***

## **Change File Ownership (chown)**

The `chown` command is used to change the ownership of a file or directory.

### **Change Owner**

Change the owner of a file.

```bash
chown user file_name
```

### **Change Group**

Change the group ownership of a file.

```bash
chown :group file_name
```

### **Change Owner and Group**

Change both the owner and group of a file.

```bash
chown user:group file_name
```

### **Recursive Ownership Change**

Apply ownership changes to all files and directories within a directory.

```bash
chown -R user:group directory_name
```

***

### **Examples**

*   Set permissions for a script file to be executable by all users:

    ```bash
    chmod 755 script.sh
    ```
*   Make a file readable and writable by the owner only:

    ```bash
    chmod 600 secret.txt
    ```
*   Change ownership of a file to `user1` and group to `developers`:

    ```bash
    chown user1:developers project.doc


    ```
