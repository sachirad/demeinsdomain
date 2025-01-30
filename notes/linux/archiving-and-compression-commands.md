# Archiving and Compression Commands

## **Archiving with `tar`**

The `tar` command is used to create archives of files and directories.

### **Basic Commands**

*   Create an archive:

    ```bash
    tar -cvf archive.tar file_or_directory
    ```

    * `-c`: Create a new archive
    * `-v`: Verbose mode (list files being archived)
    * `-f`: Specify the name of the archive file
*   Extract an archive:

    ```bash
    tar -xvf archive.tar
    ```

    * `-x`: Extract files from the archive
*   View the contents of an archive:

    ```bash
    tar -tvf archive.tar
    ```

    * `-t`: List the contents of the archive
*   Create a compressed archive:

    ```bash
    tar -czvf archive.tar.gz file_or_directory
    ```

    * `-z`: Compress the archive using gzip
*   Extract a compressed archive:

    ```bash
    tar -xzvf archive.tar.gz
    ```

***

## **Compression with `gzip`**

The `gzip` command compresses files using the Gzip format.

### **Basic Commands**

*   Compress a file:

    ```bash
    gzip file_name
    ```

    * This replaces the original file with a `.gz` compressed version.
*   Decompress a file:

    ```bash
    gunzip file_name.gz
    ```

    * Restores the original file from the compressed `.gz` file.

***

## **Compression with `bzip2`**

The `bzip2` command compresses files using the Bzip2 format, offering better compression than Gzip.

### **Basic Commands**

*   Compress a file:

    ```bash
    bzip2 file_name
    ```

    * This replaces the original file with a `.bz2` compressed version.
*   Decompress a file:

    ```bash
    bunzip2 file_name.bz2
    ```

    * Restores the original file from the compressed `.bz2` file.

***

## **Compression with `zip`**

The `zip` command creates compressed archives in ZIP format.

### **Basic Commands**

*   Create a ZIP archive:

    ```bash
    zip archive.zip file1 file2
    ```
*   Add files to an existing ZIP archive:

    ```bash
    zip archive.zip additional_file
    ```
*   Compress an entire directory:

    ```bash
    zip -r archive.zip directory_name
    ```

    * `-r`: Recursively include files in directories

***

## **Extracting with `unzip`**

The `unzip` command extracts files from a ZIP archive.

### **Basic Commands**

*   Extract files from a ZIP archive:

    ```bash
    unzip archive.zip
    ```
*   List the contents of a ZIP archive without extracting:

    ```bash
    unzip -l archive.zip
    ```

***

## **Examples**

*   Create a tar archive and compress it with gzip:

    ```bash
    tar -czvf archive.tar.gz folder_name
    ```
*   Extract a `.tar.gz` archive:

    ```bash
    tar -xzvf archive.tar.gz
    ```
*   Compress a file with `gzip`:

    ```bash
    gzip document.txt
    ```
*   Decompress a `.gz` file:

    ```bash
    gunzip document.txt.gz
    ```
*   Create a ZIP archive of multiple files:

    ```bash
    zip archive.zip file1.txt file2.txt
    ```
*   Extract a ZIP archive:

    ```bash
    unzip archive.zip


    ```
