# PPID Spoofing Guide

1. First, download the code from the below GitHub repository.

{% @github-files/github-code-block url="https://github.com/sachirad/ppid_spoofing/blob/main/ppid-spoof.c" fullWidth="true" %}

2. Second, you need to compile the `ppid-spoof.c` file. For that, you need to install GCC in your system.

**Step 1**: Check whether you have GCC already installed by running:

```
gcc --version
```

* Continue the other steps only if GCC is not installed.

**Step 2**: To install GCC, download MSYS2 from [MSYS2 website](https://www.msys2.org/), install it, and open the MSYS2 terminal. Then run:

```
pacman -S mingw-w64-x86_64-gcc
```

**Step 3**: After installing GCC, add it to the System PATH:

* Open the Start Menu and search for "Environment Variables".
* Click "Edit the system environment variables".
* Click "Environment Variables".
* Under System Variables, find "Path" and click "Edit".
*   Click "New" and add:

    ```
    C:\msys64\mingw64\bin
    ```
* Click "OK" to save changes.
*   Restart Command Prompt and verify by running:

    ```
    gcc --version
    ```

3. Run the `compile.bat` file to compile `ppid-spoof.c`.

{% @github-files/github-code-block url="https://github.com/sachirad/ppid_spoofing/blob/main/compile.bat" %}

4. **Step 5**: After compilation, you will have a `ppid_spoofing.exe` file. Use it with the following command:

```
ppid_spoofing.exe <PPID> <EXE>
```

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-29 222458.png" alt=""><figcaption><p>Spoofing Notepad.exe under Spotify, OpenVPN, and Explorer</p></figcaption></figure>



<figure><img src="../../.gitbook/assets/Screenshot 2025-01-29 222305.png" alt=""><figcaption><p>Verifing Notepad.exe is spoofed</p></figcaption></figure>
