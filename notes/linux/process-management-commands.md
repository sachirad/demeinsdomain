# Process Management Commands

## **Display Active Processes (ps)**

The `ps` command provides information about active processes.

### **Basic Usage**

*   Display processes running in the current shell:

    ```bash
    ps
    ```

### **Detailed Information**

*   Show all processes with extended details:

    ```bash
    ps aux
    ```

***

## **Monitor System Processes (top)**

The `top` command provides a real-time view of system processes and resource usage.

### **Usage**

*   Start monitoring processes:

    ```bash
    top
    ```
* Press `q` to exit the `top` view.

***

## **Terminate a Process by PID (kill)**

The `kill` command sends a signal to terminate a process using its Process ID (PID).

### **Usage**

*   Terminate a process:

    ```bash
    kill PID
    ```
*   Forcefully terminate a process:

    ```bash
    kill -9 PID
    ```

***

## **Terminate All Processes by Name (killall)**

The `killall` command terminates all processes with a specific name.

### **Usage**

*   Terminate all processes with a given name:

    ```bash
    killall process_name
    ```

***

### **Examples**

*   List all active processes:

    ```bash
    ps aux
    ```
*   Monitor processes and resource usage:

    ```bash
    top
    ```
*   Kill a process with PID 1234:

    ```bash
    kill 1234
    ```
*   Kill all instances of a process named `nginx`:

    ```bash
    killall nginx


    ```
